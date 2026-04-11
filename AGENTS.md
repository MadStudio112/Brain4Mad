# AGENTS.md

Brain4Mad ist ein persistent gepflegtes Markdown-Wiki.

## Ziel
- Rohquellen in `raw/` sammeln
- Wissen als verlinkte Markdown-Seiten kompilieren
- Das Wiki laufend aktualisieren statt Antworten immer neu herzuleiten

## Schichten
- `raw/` = unveränderte Quellen, nie umschreiben
- `sources/` = Quellzusammenfassungen und Source Notes
- übrige Ordner = kompilierte Wissensseiten

## Arbeitsregeln
- Erst Quellen lesen, dann Wiki ändern
- `raw/_inbox/` als primären Eingang für Rohquellen behandeln und möglichst leer halten
- Neue Rohquellen aus `raw/_inbox/` in die passenden `raw/`-Unterordner verteilen
- Neue Erkenntnisse in bestehende Seiten integrieren statt Duplikate anzulegen
- Widersprüche explizit notieren
- `index.md` nach relevanten neuen Seiten aktualisieren
- `log.md` append-only halten
- Aussagekräftige Wikilinks pflegen
- YAML-Frontmatter kurz und konsistent halten
- Halbfertige Wiki-Seiten direkt am Zielort mit `status: draft` markieren, kein Staging-Ordner
- **Nach jedem Aufräumen von `raw/_inbox/` zwingend committen und pushen** — Inbox-Leerung ist ein atomarer Schritt, der nicht halb im Working Tree liegen bleiben darf (Multi-PC-Sync)
- **Dedup-Check vor jedem Verschieben aus `raw/_inbox/`:** per Grep nach `source:`-URL und Titel-Slug in bestehendem `raw/` prüfen. Bei inhaltlichem Treffer: identische Datei löschen (+ `log.md`-Eintrag `dedup`), aktualisierte Version als `<slug>-v1.md` archivieren, echte Konflikte in `sources/` notieren
- `raw/` wird **vollständig mit committet** (inkl. Unterordner wie `articles/`, `notes/`, `transcripts/`): dient als Provenance-Layer für `sources/` und als Basis für späteres Re-Processing. Binaries (große PDFs, Bilder, Daten-Dumps) erst dann aus Git ausschließen, wenn das Repo dadurch real aufgeht

## Bevorzugte Struktur
- `raw/` mit `raw/_inbox/`, `articles/`, `documents/`, `transcripts/`, `notes/`, `images/`, `data/`
- `projects/` als `Domain/Projektordner/` aufbauen
- `decisions/`, `mocs/`, `agent-mad/`
- `sources/`, `entities/`, `concepts/`, `topics/`, `comparisons/`, `synthesis/`, `questions/`, `timelines/`

## Dateinamen-Konvention (Wiki-Ebene)
Gilt für alle `.md` in `sources/`, `topics/`, `entities/`, `concepts/`, `comparisons/`, `synthesis/`, `questions/`, `timelines/`, `decisions/`, `mocs/` und für Projektseiten unter `projects/<domain>/<projekt>/`. **Nicht** für `raw/` — dort ist die Benennung egal, der Ordnerpfad liefert den Kontext.

- **kebab-case, lowercase, ASCII** (`ä/ö/ü` → `ae/oe/ue`, `ß` → `ss`, keine Leerzeichen/Sonderzeichen außer `-`)
- **Basename muss ohne Pfad eindeutig sein** — Obsidian-Graph und Wikilinks zeigen nur den Basename
- **Kein Nummern-Prefix** (`01-`, `02-`) — das ist `raw/notes/`-Stil, nicht Wiki
- **Projekt-Prefix bei Kollisionsgefahr** für generische Begriffe: `immolizer-open-questions.md` statt `open-questions.md`. Ausnahme: innerhalb eines Projektordners (`projects/webdev/immolizer/`) liefert der Ordner den Namespace, dort bleiben `overview.md`/`notes.md`/`tasks.md`/`decisions.md` ohne Prefix
- **Typ-Suffix nur bei echter Disambiguierung**: `teamchef.md` (topic) vs. `teamchef-source-migration.md` (source) vs. `teamchef-open-questions.md` (question)
- **Versionierung**: `<slug>-v1.md` für archivierte Vorversionen, `<slug>-YYYY-MM-DD.md` für datumsgebundene Snapshots
- **Nicht umbenennen ohne Wikilink-Migration** — jede Umbenennung verlangt Grep über alle `[[...]]`-Referenzen und Update in `index.md`

## Projekte
- Projekte standardmäßig als Ordner anlegen, nicht als Einzeldatei
- Empfohlene Form: `projects/<domain>/<projekt>/`
- Kleine Projektordner starten mit `overview.md`, `notes.md`, `decisions.md`, `tasks.md`
- Nur bei Bedarf weitere Unterseiten oder `assets/`, `sources/` ergänzen

## Agent-Arbeitsbereich `agent-mad/`
- Zwei Rollen, klar getrennt:
  - **Root-Ebene** = Wiki-Arbeitsgedächtnis: `working-context.md`, `project-radar.md`, `decision-rules.md`, `mistakes.md`, `daily/`, `patterns/`
  - **`agent-mad/openclaw/`** = Wissensbasis für den openclaw-Agent-Stack (`C:\Users\Mad\.openclaw\`)
- openclaw Runtime-SSoT bleibt in `C:\Users\Mad\.openclaw\` — `agent-mad/openclaw/` ist nur verdichtete Doku, keine Live-Spiegelung
- `.openclaw/*.md` bleiben unangetastet
- **Niemals** Secrets/Credentials/Tokens/Logs aus `.openclaw/` nach `agent-mad/` kopieren — siehe `agent-mad/README.md`

## Schreibstil
- prägnant, konkret, source-grounded
- Unsicherheit, Status und Confidence sichtbar machen
- kein Fülltext, keine Chat-Prosa
