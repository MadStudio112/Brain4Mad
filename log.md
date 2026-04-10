---
title: "Änderungsprotokoll"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-09
tags: [meta, log]
confidence: high
---

# Änderungsprotokoll

Append-only-Verlauf relevanter Wiki-Änderungen.

## [2026-04-09] init | Wiki-Grundstruktur erstellt

- Neue Seiten: `index.md`, `log.md`, `overview.md`
- Verzeichnisse: `sources/`, `entities/`, `concepts/`, `topics/`, `comparisons/`, `synthesis/`, `open_questions/`, `timelines/`
- Status: Basis nach LLM-Wiki-Muster angelegt
- Offene Frage: Welche Domäne wird zuerst aufgebaut?

## [2026-04-09] restructure | Brain4Mad auf persistentes LLM-Wiki erweitert

- Neue Zielstruktur festgelegt: `raw/`, `inbox/`, `projects/`, `decisions/`, `mocs/`, `questions/`
- `open_questions/` fachlich durch `questions/` ersetzt
- `overview.md` und `index.md` auf die neue Struktur angepasst
- `AGENTS.md` für Wiki-Regeln ergänzt
- Skill für Brain4Mad/Obsidian geplant

## [2026-04-09] ingest | WORKxs Brainstorming verarbeitet

- Rohquelle aus `raw/_inbox/` nach `raw/notes/WORKxs - Brainstorming.md` verschoben
- Source Note `[[workxs-brainstorming]]` angelegt
- Thema `[[workxs]]` angelegt
- Offene Fragen in `[[workxs-open-questions]]` ausgelagert
- Wettbewerbsvergleich `[[workxs-competitor-landscape]]` angelegt
- Wettbewerber als erste Entity-Seiten ergänzt

## [2026-04-09] migrate | Immolizer aus Nextra-Wiki ins Brain überführt

- Ordner `C:\Users\Mad\Code\MadStudio112\Wiki\nextra\src\content\immolizer` nach `raw/notes/immolizer/immolizer/` verschoben
- Projektordner `projects/webdev/immolizer/` angelegt
- Projektseiten `overview.md`, `notes.md`, `tasks.md` ergänzt
- Source Note `[[immolizer-source-migration]]` angelegt
- Topic `[[immolizer]]`, Fragen-Seite `[[immolizer-open-questions]]` und MOC `[[immolizer-raw-structure]]` ergänzt

## [2026-04-09] migrate | TeamChef-Brainstorming ins Brain überführt

- Ordner `C:\Users\Mad\Code\MadStudio112\Wiki\nextra\src\content\teamchef\brainstorming` nach `raw/notes/teamchef/brainstorming/` verschoben
- Projektordner `projects/webdev/teamchef/` angelegt
- Projektseiten `overview.md`, `notes.md`, `tasks.md` ergänzt
- Source Note `[[teamchef-source-migration]]` angelegt
- Topic `[[teamchef]]`, Fragen-Seite `[[teamchef-open-questions]]` und MOC `[[teamchef-raw-structure]]` ergänzt

## [2026-04-09] refine | Privaten Agent-Bereich auf `agent-mad/` umgestellt

- `agent-openclaw/` nach `agent-mad/` umbenannt
- `working-context.md`, `project-radar.md`, `decision-rules.md`, `mistakes.md` ergänzt
- `daily/` und `patterns/` als Arbeitsgedächtnis-Struktur ergänzt
- AGENTS.md, Index und Skill auf `agent-mad/` umgestellt

## [2026-04-09] inventory | Webdev-Portfolio in Brain4Mad angelegt

- Root-Ordner in `C:\Users\Mad\Code\MadStudio112` inventarisiert
- `mocs/webdev-overview.md` als Portfolio-Einstieg angelegt
- Für mehrere Webdev- und Tooling-Repos Projektordner unter `projects/webdev/` angelegt
- Erste Minimal-Overviews für Lawrank, Repo Dashboard, SaaS-360, teamradar, Warren, ui_designer, mad-agent, AI-HUB, Immolizer v0, TeamChef v0 und WORKxs Repo ergänzt
- `agent-mad/project-radar.md` auf das breitere Portfolio erweitert

## [2026-04-09] cluster | Repo-Familien und Hauptanker definiert

- Webdev-Portfolio in Familien gegliedert: Immolizer, TeamChef, WORKxs, einzelne Produktprojekte und interne Plattformen
- `comparisons/webdev-project-families.md` angelegt
- `mocs/webdev-overview.md` von bloßer Liste auf Familienlogik umgebaut
- Thema-Seiten für Lawrank, Repo Dashboard, SaaS-360, teamradar, Warren, UI Designer, mad-agent und AI-HUB ergänzt
- Project Radar auf kanonische Hauptanker statt lose Repo-Liste geschärft

## [2026-04-09] research | EU Real Estate Platform Landscape ingested

- Source Note `[[eu-real-estate-platforms-research]]` angelegt (Methodik, Konfidenz-Hinweise, Konzernstruktur-Übersicht)
- Topic `[[eu-real-estate-platform-landscape]]` angelegt (strukturelle Muster, pan-europäische Akteure, Relevanz für Immolizer)
- Vier regionale Vergleichsseiten angelegt:
  - `[[eu-re-platforms-western]]` — DE, AT, FR, NL, BE, LU, IE
  - `[[eu-re-platforms-southern]]` — ES, PT, IT, GR, MT, CY
  - `[[eu-re-platforms-northern]]` — SE, DK, FI
  - `[[eu-re-platforms-eastern]]` — PL, CZ, HU, RO, BG, HR, SK, SI, EE, LV, LT
- Abdeckung: alle 27 EU-Mitgliedstaaten; je bis zu 3 Plattformen pro Land
- Datenbasis: LLM-Wissen ~2024 + vereinzelte Web-Fetches (Scout24.com, Funda.nl, Wikipedia/Daft.ie, Wikipedia/LeBonCoin)
- Konfidenz: mittel für Westeuropa, niedrig für Osteuropa; Traffic-Zahlen Schätzwerte; Ownership CEE oft unsicher
- Index und Log aktualisiert

## [2026-04-09] prioritize | Webdev-Portfolio priorisiert

- `comparisons/webdev-priority-map.md` angelegt
- `mocs/webdev-overview.md` um Core, Secondary, Internal Infrastructure und Archive/Legacy erweitert
- `agent-mad/project-radar.md` von Domain-Sicht auf Bucket-Sicht umgestellt
- Core-Fokus aktuell auf Immolizer, TeamChef und WORKxs gesetzt
