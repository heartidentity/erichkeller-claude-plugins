# Redaktions-Plugin für erichkeller.ch

Claude-Plugin für Editoren: Referenzen erfassen und CMS-Seiten bauen, direkt
in DatoCMS (via offiziellem DatoCMS-MCP, OAuth im Browser).

**Dieses Verzeichnis ist die Quelle.** Ausgeliefert wird das Plugin über den
Marketplace [`heartidentity/erichkeller-claude-plugins`](https://github.com/heartidentity/erichkeller-claude-plugins) —
der Workflow [`publish-editors-plugin.yml`](../.github/workflows/publish-editors-plugin.yml)
spiegelt Änderungen bei jedem Push auf `develop` dorthin. Im Marketplace-Repo
nie von Hand editieren.

## Inhalt

- `skills/referenz-erfassen/` — geführtes Erfassen einer Referenz (Pflichtfelder-
  Interview, Taxonomie aus bestehenden Records, Draft + Preview-Hinweis)
- `skills/seite-bauen/` — Seitenaufbau mit Block-Katalog und Kompositionsregeln
  (Beispielseiten zuerst, Struktur-Okay vor dem Anlegen)
- `docs/redaktions-regeln.md` — gemeinsame Grundregeln (nur Drafts, nie
  publizieren/löschen, kein Schema, Sprachen, Bild-Handling)
- `.mcp.json` — DatoCMS Remote-MCP (`https://mcp.datocms.com`)

## Release

Version in `.claude-plugin/plugin.json` bumpen — **jede inhaltliche Änderung
braucht einen Bump**, sonst schlägt der Publish-Workflow fehl (und Cowork
würde die alte Version behalten). Cowork aktualisiert installierte Plugins
beim Start auf die neueste Marketplace-Version.

## Installation (Editoren)

Einmalig in Cowork / Claude Code:

1. Marketplace hinzufügen: `heartidentity/erichkeller-claude-plugins`
   (privates Repo — GitHub-Zugriff nötig, Lesezugriff genügt)
2. Plugin `redaktion` installieren
3. Beim ersten DatoCMS-Zugriff öffnet sich der OAuth-Login — mit dem
   DatoCMS-Konto des Editors anmelden (Rechte = Dato-Rolle des Editors)
