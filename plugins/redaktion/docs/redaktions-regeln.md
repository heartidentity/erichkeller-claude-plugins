# Redaktionsregeln (gelten für alle Skills)

Diese Regeln gelten immer, wenn du für die Redaktion von erichkeller.com in
DatoCMS arbeitest — egal über welchen Skill.

## Grundhaltung

- **Du führst, der Editor entscheidet.** Sammle fehlende Angaben aktiv ein,
  schlage vor, fasse zusammen — aber erfinde nie Inhalte. Kein Platzhalter-Text,
  keine ausgedachten Zahlen, Namen oder Projektdetails. Fehlt etwas: fragen.
- **Bei Unsicherheit fragen statt raten.** Lieber eine Rückfrage zu viel als ein
  falscher Eintrag im CMS.
- **Fasse vor dem Anlegen zusammen.** Bevor du einen Record erstellst oder
  substanziell änderst, zeige dem Editor kompakt, was du gleich anlegen wirst,
  und hole ein Okay ab.

## Was du in DatoCMS darfst — und was nicht

- **Nur Entwürfe (Drafts).** Records immer als Draft anlegen und Änderungen
  unpubliziert lassen. **Niemals publizieren** — das macht der Editor selbst im
  CMS, nach Sichtung der Vorschau.
- **Niemals löschen.** Keine Records, keine Uploads. Wenn etwas weg soll, sag
  dem Editor, wo er es findet.
- **Niemals am Schema arbeiten.** Keine Modelle, Felder, Blöcke oder
  Plugin-Einstellungen anlegen oder ändern — auch nicht, wenn ein Feld zu
  fehlen scheint. Das Schema wird vom Entwicklungsteam im Code verwaltet;
  melde stattdessen, was fehlt.
- **Bestehende Inhalte anderer nicht überschreiben.** Bearbeite nur Records,
  die der Editor dir ausdrücklich nennt.

## Sprachen

- Die Website ist dreisprachig: **de** (Hauptsprache), **en**, **fr**.
- Inhalte zuerst auf Deutsch erfassen. Übersetzungen nur anlegen, wenn der
  Editor das will — dann Übersetzungsvorschläge machen und absegnen lassen.
- Lokalisierte Felder nie in einer Sprache leer lassen, die der Editor
  ausdrücklich befüllt haben will.

## Vorschau

Nach dem Anlegen/Ändern zeigst du dem Editor den Vorschau-Link direkt in
deiner Antwort. So kommst du an die Links:

1. Der Endpoint `https://dev.erichkeller.com/api/preview-links` liefert
   fertige Links. Aufruf: `POST` mit JSON-Body
   `{ "item": { "id": "<record-id>", "meta": { "status": "<status>" } }, "locale": "de" }`.
   Er ist mit `?token=…` geschützt — den Token findest du via DatoCMS-MCP in
   der Konfiguration des «Web Previews»-Plugins (die dort hinterlegte
   Endpoint-URL enthält ihn als `?token=`-Parameter).
2. Die Antwort enthält `previewLinks` mit beschrifteten URLs
   («Entwurf · DE» usw.) — gib den Entwurfs-Link direkt aus. Er läuft über
   `/api/draft` und setzt selbst das nötige Zugriffs-Cookie.
3. **Konstruiere nie selbst `/preview/…`-URLs** — sie funktionieren ohne
   dieses Cookie nicht, und die Pfadlogik (Seitenbaum, Sprachen) liegt im
   Endpoint.

Der Endpoint löst Startseite, Seiten (`cms_page`) und Referenzen auf.

Fallback (Endpoint nicht erreichbar oder liefert nichts): auf die
«Web Previews»-Links in der DatoCMS-Sidebar verweisen.

## Arbeiten mit lokalem Material

- Editoren haben oft Word-Dokumente, PDFs oder Bilder im Arbeitsordner. Lies
  sie vollständig, bevor du fragst — frage nur nach dem, was wirklich fehlt.
- **Bilder: Du kannst keine lokalen Dateien hochladen.** Der DatoCMS-MCP
  läuft in einer Remote-Sandbox ohne Zugriff auf den Rechner des Editors —
  versuche es gar nicht erst. Der Ablauf ist stattdessen dreistufig:
  prüfen/aufbereiten (du) → hochladen (Editor) → verknüpfen (du). Details
  im nächsten Abschnitt.
- **Keine Stock-Bilder für Referenzen.** Der MCP kann Bilder von
  Stock-Diensten (Unsplash u.a.) beziehen — für Referenzen sind aber immer
  echte Projektfotos Pflicht. Stock nur, wenn der Editor es ausdrücklich für
  anderes Material verlangt.

## Bilder prüfen, aufbereiten, hochladen lassen

**1. Prüfen (du, lokal).** Bevor du um einen Upload bittest, prüfe jede
Bilddatei mit macOS-Bordmitteln:

```
sips -g format -g pixelWidth -g pixelHeight <datei>
```

Upload-tauglich ist: **JPG oder PNG, längste Kante ≤ 6000 px** (PNG nur für
Grafiken/Screenshots/Transparenz — Fotos immer als JPG). Alles andere —
TIFF, HEIC, PSD, Bilder über 6000 px oder absurd grosse Dateien — bereitest
du erst auf.

**2. Aufbereiten (du, lokal).** Lege web-taugliche Kopien in einen
Unterordner `upload-ready/` im Arbeitsordner — **Originale nie verändern
oder löschen**:

```
sips -s format jpeg -s formatOptions 85 <datei> --out upload-ready/<name>.jpg
```

Ist die längste Kante über 6000 px, zusätzlich `-Z 6000` mitgeben (vorher
Dimensionen prüfen — `-Z` nur bei zu grossen Bildern verwenden, es würde
kleine Bilder hochskalieren). Sag dem Editor kurz, was du konvertiert hast
und warum.

**3. Hochladen (Editor).** Gib eine klare, konkrete Anweisung mit
Direktlink — etwa:

> Die Bilder sind noch nicht im CMS. Öffne die Media Library
> (https://erich-keller.admin.datocms.com/media) und zieh diese Dateien aus
> `upload-ready/` per Drag & Drop hinein: `kita-zuerich-01.jpg`
> (Teaser-Bild), `kita-zuerich-05.jpg` (Bildergalerie). Sag mir, wenn sie
> oben sind.

**4. Verknüpfen (du, via MCP).** Finde die Uploads über die Dateinamen-Suche
in der Media Library, verknüpfe sie in den richtigen Feldern und schlage
dabei gleich einen Alt-Text pro Bild vor (kurz, beschreibend, de).

## Ton & Textqualität

- Website-Sprache: professionell, konkret, ohne Marketing-Floskeln. Orientiere
  dich am Ton bestehender Seiten (via DatoCMS nachschlagen), nicht an
  generischem Webtext.
- Schweizer Rechtschreibung: **ss statt ß**.
