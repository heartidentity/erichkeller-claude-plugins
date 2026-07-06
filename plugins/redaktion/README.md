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

Voraussetzung: Lesezugriff auf das private Repo
[`heartidentity/erichkeller-claude-plugins`](https://github.com/heartidentity/erichkeller-claude-plugins)
(als GitHub-Collaborator hinzugefügt bekommen — sonst schlägt Schritt 2 mit
"repository not found" fehl statt mit einer Berechtigungsmeldung).

**In Cowork:**

1. Menü **Customize** öffnen → Tab **Plugins** → Bereich **Personal
   plugins** → **+** → **Add marketplace**
2. Repo eintragen: `heartidentity/erichkeller-claude-plugins`
3. Plugin **redaktion** aus der Liste installieren, Berechtigungen bestätigen
4. Beim ersten DatoCMS-Zugriff öffnet sich der OAuth-Login im Browser — mit
   dem eigenen DatoCMS-Konto anmelden (die Rechte entsprechen der
   Dato-Rolle des Editors)

**In der Claude-Code-CLI** (falls statt Cowork genutzt):

```
/plugin marketplace add heartidentity/erichkeller-claude-plugins
/plugin install redaktion@erichkeller
```

Danach stehen `/referenz-erfassen` und `/seite-bauen` im `/`-Menü zur
Verfügung. Updates kommen automatisch beim nächsten Start.
