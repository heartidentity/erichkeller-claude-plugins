---
name: seite-bauen
description: Eine CMS-Seite für erichkeller.ch in DatoCMS aufbauen oder umbauen — Header und Sections aus dem Block-Katalog zusammenstellen. Nutzen, wenn der Editor eine Seite anlegen, aufbauen, erweitern oder umstrukturieren will.
---

# Seite bauen

Du hilfst einem Editor, eine Seite (`cms_page`) im DatoCMS von erichkeller.ch
aufzubauen. Lies zuerst `${CLAUDE_PLUGIN_ROOT}/docs/redaktions-regeln.md` —
diese Regeln gelten verbindlich (nur Drafts, nie erfinden, nie publizieren).

## Ablauf

1. **Erst Beispiele, dann bauen.** Bevor du irgendetwas anlegst: Hole via
   DatoCMS-MCP **2–3 publizierte Seiten ähnlichen Typs** (gleiche Ebene im
   Seitenbaum, ähnlicher Zweck) und analysiere ihre Blockfolge. Baue neue
   Seiten nach diesen Mustern, nicht nach eigenem Geschmack. Nenne dem Editor
   kurz, an welchen Seiten du dich orientierst.
2. **Einordnung klären.** Wo im Seitenbaum hängt die Seite (Elternseite)?
   `cms_page` ist ein Baum — die URL ergibt sich aus dem Pfad. Ohne klare
   Elternseite: nachfragen.
3. **Struktur vorschlagen.** Schlage Header + Section-Abfolge als kompakte
   Gliederung vor (Block + einzeiliger Inhalt je Section) und hole das Okay
   ab, **bevor** du Records anlegst.
4. **Als Draft anlegen**, danach den Vorschau-Link gemäss Redaktionsregeln
   holen und direkt in der Antwort anzeigen.

## Header: genau ein Block

- `page_intro` — Standard für die meisten Seiten: Titel, Lead, Bild.
- `hero_slider` — grosse Bühne mit Slides; nur für Startseiten-artige
  Einstiegsseiten.
- `statement_media_section` — Aussage + Medium; für Seiten, die mit einer
  These statt einem klassischen Intro starten.

## Section-Katalog (Kurzreferenz)

Das CMS ist die Wahrheit — hole die aktuelle Blockliste via MCP, wenn etwas
fehlt oder unklar ist. Zweck der Blöcke:

**Text & Inhalt**
- `richtext_block` — Fliesstext (die einfachste Wahl für Prosa).
- `content_with_media_section` — Text neben Bild/Video; das Arbeitspferd für
  erklärende Abschnitte.
- `text_columns_section` — kurzer Text in Spalten.
- `accordion` — auf-/zuklappbare Punkte (FAQ, Detailinfos).
- `quote_section` — Zitat, z.B. Kundenstimme.

**Zahlen & Fakten**
- `stats_section` — wenige grosse Kennzahlen.
- `facts_figures_section` — Zahlen & Fakten als Liste/Tabelle.
- `pikto_section` — Punkte mit Piktogrammen.

**Medien & Inszenierung**
- `media_block` — einzelnes Bild/Video in gross.
- `image_marquee` — durchlaufendes Bildband (volle Breite).
- `sticky_scroll_section` — Text-Media-Sequenz mit Scroll-Effekt; sparsam
  einsetzen, max. eine pro Seite.
- `statement_media_section` — Aussage + Medium (auch als Section möglich).
- `tabs_with_media_section` — Inhalte in Tabs mit Medium.
- `airflow_animation` — dekorative Luftstrom-Animation; Spezialfall, nur wo
  bereits etabliert.

**Teaser & Sammlungen**
- `reference_teasers_section` — handverlesene Referenzen anteasern.
- `teaser_collection_section` — Teaser auf beliebige Inhalte.
- `collection_section` — automatische, filterbare Übersicht (z.B. alle
  Referenzen); gehört auf Übersichtsseiten, nicht mitten in Inhaltsseiten.
- `card_grid` — Karten-Raster.
- `link_list` — Linkliste.
- `solution_slider` — Slider über die Lösungen.
- `product_detail_section` — Produktdetails mit Sticky-Navigation; nur auf
  Produkt-/Lösungsseiten.

**Funktional**
- `contact_cta` — Kontakt-Aufforderung; Standard-Abschluss fast jeder Seite.
- `hubspot_form_section` — eingebettetes Formular.
- `job_listing_section` — offene Stellen (automatisch aus dem Jobtool).
- `downloads_section` — Downloads/Dokumente.

## Kompositionsregeln

- **Abwechslung vor Wiederholung.** Nicht zwei gleiche Blocktypen direkt
  hintereinander; auf einen textlastigen Block folgt idealerweise ein
  visueller (Medien, Zahlen, Teaser).
- **Hintergrund-Bänder beachten:** Aufeinanderfolgende Sections mit gleicher
  Hintergrundfarbe verschmelzen optisch zu einem Band. Das ist gewollt — aber
  eine ganze Seite ohne Farbwechsel wirkt monoton. Bewusst gruppieren.
- **Eine Inszenierung pro Seite.** Effektlastige Blöcke (`sticky_scroll_section`,
  `image_marquee`, `airflow_animation`, `hero_slider`) maximal je einmal
  einsetzen.
- **`contact_cta` steht am Schluss** — und nur einmal.
- **Übersicht vs. Inhalt trennen:** `collection_section` und
  `job_listing_section` tragen eine Seite (Übersichtsseite), sie sind kein
  Zwischenelement.
- **Weniger ist okay.** Eine gute Seite hat oft nur 3–5 Sections. Schlage
  nicht mehr Blöcke vor, als Inhalt vorhanden ist.
