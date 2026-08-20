---
name: referenz-erfassen
description: Eine neue Referenz (Projekt) für erichkeller.com in DatoCMS erfassen oder eine bestehende vervollständigen. Nutzen, wenn der Editor eine Referenz, ein Projekt oder einen Case erfassen, anlegen oder überarbeiten will — auch aus Word-Dokumenten oder Notizen.
---

# Referenz erfassen

Du hilfst einem Editor, eine Referenz (ein realisiertes Projekt) im DatoCMS von
erichkeller.com zu erfassen. Lies zuerst
`${CLAUDE_PLUGIN_ROOT}/docs/redaktions-regeln.md` — diese Regeln gelten
verbindlich (nur Drafts, nie erfinden, nie publizieren).

## Ablauf

1. **Material sichten.** Liegt lokales Material vor (Word, PDF, Notizen,
   Bilder), lies es vollständig. Extrahiere alles, was du den Feldern unten
   zuordnen kannst.
2. **Schema-Referenz und Beispiele laden.** Die vollständige Feld-Referenz
   (Modell `reference`, Taxonomien, Block-Katalog mit Feldern, Pflichtfeldern
   und Enum-Werten) liegt lokal in
   `${CLAUDE_PLUGIN_ROOT}/skills/referenz-erfassen/references/schema.md` —
   lies sie statt das Schema via MCP zu holen. Nur bei Unklarheiten oder wenn
   dort etwas zu fehlen scheint, via DatoCMS-MCP nachschlagen (das CMS bleibt
   die Wahrheit). Schau dir zusätzlich via MCP 1–2 bestehende, publizierte
   Referenzen an: Feldnutzung, Textlänge, Tonalität, typischer Seitenaufbau.
3. **Lücken identifizieren und nachfragen.** Gleiche das Material mit der
   Checkliste unten ab. Frage den Editor **gesammelt und konkret** nach allem,
   was fehlt — eine übersichtliche Liste, nicht zehn Einzelfragen. Erfinde
   nichts, auch keine «vorläufigen» Werte.
4. **Zusammenfassen und Okay einholen.** Zeige kompakt, was du anlegen wirst
   (Titel, Zuordnungen, Seitenaufbau), und warte auf Bestätigung.
5. **Als Draft anlegen.** Nutze die fertigen Script-Rezepte in
   `${CLAUDE_PLUGIN_ROOT}/docs/cma-rezepte.md` (Taxonomien laden,
   Referenz-Draft anlegen, Vorschau-Link holen). Danach den Vorschau-Link
   gemäss Redaktionsregeln direkt anzeigen. Publizieren liegt beim Editor.

## Checkliste: Was eine Referenz braucht

Pflicht — ohne diese Angaben nicht anlegen:

- **Titel** (`title`, de): prägnanter Projektname, wie er auf der Website
  erscheinen soll. Der Slug wird daraus abgeleitet.
- **Teaser-Bild** (`teaser_image`): das Bild, mit dem die Referenz in
  Übersichten erscheint. Muss in der Media Library liegen (siehe
  Redaktionsregeln zu Bild-Uploads).
- **Referenz-Attribute** — sie steuern die Filter der Referenz-Übersicht und
  müssen darum sauber gesetzt sein:
  - `project_types` (Projektart), `industries` (Branche), `solutions`
    (Lösungen): **immer aus den bestehenden Records wählen** — die Einträge
    mit einem einzigen Script laden (Rezept «Taxonomien laden» in
    `${CLAUDE_PLUGIN_ROOT}/docs/cma-rezepte.md`) und dem Editor zur Auswahl
    vorlegen. Keine neuen Taxonomie-Einträge anlegen, ohne explizit
    nachzufragen.
  - `characteristics` (Merkmale): sind **je einer Lösung zugeordnet** — nur
    Merkmale anbieten, die zu den gewählten `solutions` gehören.
  - `products`: die im Projekt eingesetzten Produkte, aus den bestehenden
    Produkt-Records.
  - `volume` (Projektvolumen): genau eine der Stufen «bis 50 000», «50 000 –
    250 000», «250 000 – 1 Mio.», «über 1 Mio.» (CHF). Im Zweifel den Editor
    einordnen lassen.

Dringend empfohlen — aktiv nachfragen, aber der Editor darf «später» sagen:

- **Header**: genau **ein** Block — für Referenzen in der Regel `page_intro`
  (Titel + Lead + Bild). Lead-Text aus dem Material ableiten und absegnen
  lassen.
- **Sections** (Seiteninhalt): Aufbau an bestehenden Referenzen orientieren.
  Bewährtes Grundmuster: Projektbeschrieb (`content_with_media_section` oder
  `richtext_block`) → Bilder (`media_block`) → ggf. Zahlen
  (`facts_figures_section`) → Zitat des Kunden (`quote_section`) →
  `contact_cta` am Schluss. Für Details zum Block-Katalog gilt der Skill
  «seite-bauen».
- **SEO** (`seo`): Meta-Titel und -Beschreibung vorschlagen (Beschreibung
  ~150–160 Zeichen, konkret, mit Projektart und Ort falls vorhanden).

## Typische Stolperfallen

- Merkmale (`characteristics`) gesetzt, die nicht zu den gewählten Lösungen
  gehören → Filter der Übersicht zeigen die Referenz falsch an.
- Teaser-Bild vergessen → Referenz erscheint ohne Bild in allen Übersichten.
- Slug von Hand «verschönern»: nicht nötig, er wird aus dem Titel abgeleitet.
  Nur anpassen, wenn der Editor es verlangt.
