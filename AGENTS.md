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

## Bevorzugte Struktur
- `raw/` mit `raw/_inbox/`, `articles/`, `documents/`, `transcripts/`, `notes/`, `images/`, `data/`
- `projects/` als `Domain/Projektordner/` aufbauen
- `decisions/`, `mocs/`, `agent-mad/`
- `sources/`, `entities/`, `concepts/`, `topics/`, `comparisons/`, `synthesis/`, `questions/`, `timelines/`

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
