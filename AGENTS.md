# AGENTS.md

Brain4Mad ist ein persistent gepflegtes Markdown-Wiki.

## Ziel
- Rohquellen in `raw/` sammeln
- Wissen als verlinkte Markdown-Seiten kompilieren
- Das Wiki laufend aktualisieren statt Antworten immer neu herzuleiten

## Schichten
- `raw/` = unveränderte Quellen, nie umschreiben
- `projects/<domain>/<projekt>/` = Hauptarbeitsbereich, fraktal nach Projekten
- `reference/` = echtes Cross-Project-Wissen (initial leer, nur bei Bedarf befüllen)
- `agent-mad/` = Arbeitsgedächtnis des Agents

## Arbeitsregeln
- Erst relevante Quellen in `raw/` lesen, dann Wiki ändern
- `raw/_inbox/` als primären Eingang für Rohquellen behandeln und möglichst leer halten
- Neue Rohquellen aus `raw/_inbox/` in die passenden `raw/`-Unterordner verteilen
- Neue Erkenntnisse in bestehende Projektseiten integrieren statt Duplikate anzulegen
- Widersprüche explizit notieren
- `index.md` nach relevanten neuen Seiten aktualisieren
- `log.md` append-only halten
- Wikilinks pflegen, YAML-Frontmatter kurz und konsistent halten
- **Kein Inline-Tag** (`#tag`) im Fließtext — nur `tags: [...]` im Frontmatter
- **Kein `tasks.md`** in Projektordnern — Aufgaben gehören nicht ins Wiki
- Halbfertige Wiki-Seiten direkt am Zielort mit `status: draft` markieren, kein Staging-Ordner
- **Fraktaler Default:** neuer Inhalt geht in `projects/<p>/`, nicht in `reference/`. Erst nach Bedarf aus ≥2 Projekten nach `reference/` promoten
- **Nach jedem Aufräumen von `raw/_inbox/` zwingend committen und pushen** — Inbox-Leerung ist ein atomarer Schritt, der nicht halb im Working Tree liegen bleiben darf (Multi-PC-Sync)
- **Dedup-Check vor jedem Verschieben aus `raw/_inbox/`:** per Grep nach `source:`-URL und Titel-Slug in bestehendem `raw/` prüfen. Bei inhaltlichem Treffer: identische Datei löschen (+ `log.md`-Eintrag `dedup`), aktualisierte Version als `<slug>-v1.md` archivieren, echte Konflikte in Projektseite notieren
- `raw/` wird **vollständig mit committet** (inkl. Unterordner wie `articles/`, `notes/`, `transcripts/`): dient als Provenance-Layer und Basis für späteres Re-Processing. Binaries erst dann aus Git ausschließen, wenn das Repo dadurch real aufgeht

## Bevorzugte Struktur
- `raw/` mit `raw/_inbox/`, `articles/`, `documents/`, `transcripts/`, `notes/`, `images/`, `data/`, `mmap/`
- `projects/webdev/` — Web-/Software-Projekte; `projects/research/` — Themen ohne Code; `projects/personal/` — Privates
- Projektordner: `overview.md`, optional `notes.md`, `questions.md`, `brief.md`, `decisions.md`, `_raw-structure.md`
- Familien-Klammer: `projects/webdev/_familienname.md` (Underscore-Prefix, Obsidian sortiert oben)
- `reference/` — initial leer
- `agent-mad/`
- Root: `index.md`, `log.md`, `overview.md`, `CLAUDE.md`, `AGENTS.md`

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
- Projekte als Ordner anlegen: `projects/<domain>/<projekt>/`
- Standard-Dateien: `overview.md`, optional `notes.md`, `questions.md`, `brief.md`, `decisions.md`, `_raw-structure.md`
- **Kein `tasks.md`** — Aufgaben gehören nicht ins Wiki
- Familien-Klammer als `_familienname.md` im Parent-Ordner (Underscore-Prefix)
- Geschwister-Varianten als Geschwisterordner: `immolizer/`, `immolizer-v0/`, `immolizer-public/`

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
