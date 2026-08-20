# CMA-Script-Rezepte

Fertige Scripts für die häufigsten Redaktions-Operationen, ausgeführt über den
DatoCMS-MCP: `upsert_and_execute_safe_script` für reine Lese-Operationen,
`upsert_and_execute_unsafe_script` für Anlegen/Ändern. Die Feld-Referenz dazu
liegt im jeweiligen Skill unter `references/schema.md`.

## So führst du ein Script aus

1. **Method-Tokens holen:** ein einziger `get_api_methods`-Aufruf mit allen
   `{ resource, method }`-Paaren, die im Script vorkommen (z.B.
   `{ resource: "items", method: "create" }`). Die Antwort liefert pro Methode
   ein Token und die exakte Signatur — sie ist massgeblich, falls ein Rezept
   hier von der Realität abweicht.
2. **Script ausführen** via `upsert_and_execute_*_script`, alle Tokens in
   `method_tokens` mitgeben.
3. **Bei Compile-Fehlern:** Meldung lesen und mit `body.mode: "patch"`
   nachbessern statt alles neu zu schreiben.

Im Script sind `client` (CMA-Client) und `Schema` (Projekt-Typen) als Globals
verfügbar, ebenso alle Exporte von `@datocms/cma-client-node` — insbesondere
`buildBlockRecord`. Top-Level-`await` ist erlaubt, Ausgabe via `console.log`.
Verboten: `any`, `unknown`, `@ts-ignore`.

**Redaktionsregeln gelten immer:** nur Drafts anlegen/ändern, nie `publish`,
nie `destroy`, nie am Schema arbeiten (siehe `docs/redaktions-regeln.md`).

### Schema-Marker & Wert-Formate

`Schema.<PascalCase des api_key>` — `reference` → `Schema.Reference`,
`cms_page` → `Schema.CmsPage`, `quote_section` → `Schema.QuoteSection`.
Als `item_type` im Payload dient `Schema.X.REF`.

| Feldtyp | Wert im Payload |
| --- | --- |
| string / text | `"…"` |
| slug | `"kebab-case-string"` |
| file | `{ upload_id: "…" }` |
| gallery | `[{ upload_id: "…" }, …]` |
| link | Record-ID als String |
| links | `["id1", "id2"]` |
| seo | `{ title, description, image: <upload-id \| null>, twitter_card: null }` — `no_index` weglassen (nur `boolean`, kein `null`) |
| rich_text (Modular Content) | Array: neue Blöcke als `buildBlockRecord<Schema.X>({ item_type: Schema.X.REF, … })`, **bestehende Blöcke unverändert als ID-String weiterreichen** |
| structured_text | DAST-Dokument (`datocms-structured-text-utils`-Helfer sind als Globals verfügbar) |
| lokalisiert (Lok ✓) | `{ de: …, en: …, fr: … }` — immer alle drei Keys, Wert darf `null` sein |

---

## Rezept 1: Referenz-Draft anlegen

Tokens: `{ resource: "items", method: "create" }` · Tool: **unsafe**.
Neue Records entstehen automatisch als Draft — nichts publizieren.

```ts
const reference = await client.items.create<Schema.Reference>({
	item_type: Schema.Reference.REF,
	title: { de: "Kita Grünmatt Zürich", en: null, fr: null },
	slug: { de: "kita-gruenmatt-zuerich", en: null, fr: null },
	teaser_image: { upload_id: "UPLOAD_ID" },
	// Taxonomie-IDs zuerst mit Rezept 4 laden — nur bestehende Records verwenden!
	project_types: ["PROJECT_TYPE_ID"],
	industries: ["INDUSTRY_ID"],
	solutions: ["SOLUTION_ID"],
	characteristics: ["CHARACTERISTIC_ID"], // nur solche der gewählten solutions
	products: ["PRODUCT_ID"],
	volume: "up_to_50k", // up_to_50k | 50k_to_250k | 250k_to_1m | over_1m
	seo: {
		de: { title: "…", description: "…", image: null, twitter_card: null },
		en: null,
		fr: null,
	},
	header: {
		de: [
			buildBlockRecord<Schema.PageIntro>({
				item_type: Schema.PageIntro.REF,
				lead: "Lead-Text …",
				lead_style: "plain",
			}),
		],
		en: [],
		fr: [],
	},
})
console.log("Draft angelegt:", reference.id, "Status:", reference.meta.status)
```

Felder, für die noch nichts vorliegt, einfach weglassen (werden `null`).

## Rezept 2: Sections zu einer bestehenden Seite hinzufügen

Tokens: `{ resource: "items", method: "find" }` +
`{ resource: "items", method: "update" }` · Tool: **unsafe**.

Kernidee: das lokalisierte `sections`-Feld komplett zurückschreiben —
bestehende Blöcke bleiben als ID-Strings unverändert erhalten, neue kommen als
`buildBlockRecord` dazu. Funktioniert identisch für `cms_page`, `home_page`
und `reference` (Marker anpassen).

```ts
const PAGE_ID = "RECORD_ID"
const page = await client.items.find<Schema.CmsPage>(PAGE_ID)
// Ohne `nested: true` sind bestehende Blöcke ID-Strings — genau richtig,
// um sie unverändert weiterzureichen.
const sections = page.sections ?? { de: [], en: [], fr: [] }

await client.items.update<Schema.CmsPage>(PAGE_ID, {
	sections: {
		...sections, // en/fr unverändert lassen
		de: [
			...(sections.de ?? []),
			buildBlockRecord<Schema.QuoteSection>({
				item_type: Schema.QuoteSection.REF,
				quote: "«Zitat des Kunden …»",
				attribution: "Vorname Name, Firma",
			}),
		],
	},
})
console.log("Sections aktualisiert:", PAGE_ID)
```

Soll ein Block an eine bestimmte Position (z.B. vor den `contact_cta` am
Schluss), das Array entsprechend zusammensetzen statt anzuhängen. Um
bestehende Block-Inhalte zu lesen, den Record zusätzlich mit
`client.items.find(PAGE_ID, { nested: true })` holen.

## Rezept 3: Vorschau-Link holen

Tokens: `{ resource: "plugins", method: "list" }` · Tool: **safe**.

Die Sandbox darf nur DatoCMS-APIs erreichen — der Preview-Endpoint wird darum
in zwei Schritten aufgerufen: Script liefert die Endpoint-URL (inkl.
`?token=…`), der POST läuft danach lokal via Bash.

```ts
const plugins = await client.plugins.list()
const webPreviews = plugins.find(p =>
	JSON.stringify(p.parameters ?? {}).includes("/api/preview-links"),
)
if (!webPreviews)
	throw new Error("Web-Previews-Plugin nicht gefunden")
console.log(JSON.stringify(webPreviews.parameters))
```

Aus der Ausgabe die Endpoint-URL mit Token nehmen, dann lokal:

```sh
curl -s -X POST "https://dev.erichkeller.com/api/preview-links?token=…" \
  -H "Content-Type: application/json" \
  -d '{"item":{"id":"RECORD_ID","meta":{"status":"draft"}},"locale":"de"}'
```

Die Antwort enthält `previewLinks` mit beschrifteten URLs — den Entwurfs-Link
(«Entwurf · DE») direkt ausgeben. Nie eigene `/preview/…`-URLs konstruieren
(Details: `docs/redaktions-regeln.md` § Vorschau).

## Rezept 4: Alle Taxonomien in einem Durchgang laden

Tokens: `{ resource: "items", method: "list" }` · Tool: **safe**.
Liefert die Auswahl-Grundlage für Rezept 1 — inklusive der Zuordnung
Characteristic → Solution (nur Merkmale der gewählten Lösungen anbieten!).

```ts
const [projectTypes, industries, solutions, characteristics, products]
	= await Promise.all([
		client.items.list<Schema.ProjectType>({ filter: { type: "project_type" }, page: { limit: 500 } }),
		client.items.list<Schema.Industry>({ filter: { type: "industry" }, page: { limit: 500 } }),
		client.items.list<Schema.Solution>({ filter: { type: "solution" }, page: { limit: 500 } }),
		client.items.list<Schema.Characteristic>({ filter: { type: "characteristic" }, page: { limit: 500 } }),
		client.items.list<Schema.Product>({ filter: { type: "product" }, page: { limit: 500 } }),
	])

for (const t of projectTypes) console.log("project_type", t.id, t.name?.de)
for (const i of industries) console.log("industry", i.id, i.name?.de)
for (const s of solutions) console.log("solution", s.id, s.name?.de)
for (const c of characteristics) console.log("characteristic", c.id, c.name?.de, "→ solution:", c.solution)
for (const p of products) console.log("product", p.id, p.name?.de, "→ solution:", p.solution)
```
