---
title: "Änderungsprotokoll"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-10
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

## [2026-04-10] cleanup | Wiki-`inbox/` entfernt

- `inbox/` auf Wiki-Ebene gelöscht — laut CLAUDE.md gibt es nur `raw/_inbox/`
- `inbox/wc2026_matches_dewiki.json` nach `raw/data/wc2026_matches_dewiki.json` verschoben
- Duplikat `wc2026_matches_dewiki 1.json` entfernt
- `inbox/README.md` entfernt
- Verweise in `index.md`, `overview.md` und `mocs/home.md` auf `raw/_inbox/` umgestellt

## [2026-04-10] ingest | raw/_inbox abgearbeitet (Aphantasie, Aprilia, ImmoSkill, Polymarket)

- `raw/_inbox/Polymarket vs Wettanbieter.md` → `raw/articles/polymarket-vs-wettanbieter.md`
  - Source Note `[[polymarket-vs-wettanbieter]]` angelegt
  - Konzept `[[prediction-markets]]` als erste Konzept-Seite des Wikis angelegt
  - Topic `[[polymarket-trading-engine]]` (status: draft) für die Engine-Architektur angelegt

## [2026-04-10] ingest | raw/_inbox abgearbeitet (Aphantasie, Aprilia, ImmoSkill)

- `raw/_inbox/Aphantasie - Leben ohne Bilder im Kopf.md` → `raw/articles/aphantasie-dossier.md`
  - Source Note `[[aphantasie-dossier]]`, Topic `[[aphantasie]]` neu angelegt
- `raw/_inbox/Aprilia RSV 1000.md` → `raw/notes/aprilia-rsv-tuono-1000.md`
  - Source Note `[[aprilia-rsv-tuono-1000-elektrik]]`, Entity `[[aprilia-rsv-tuono-1000]]` (Kraftstoff/Killkreis-Elektrik) angelegt
- `raw/_inbox/Brainstorming - ImmoSkill.md` → `raw/notes/immoskill-brainstorming.md`
  - Source Note `[[immoskill-brainstorming]]`, Topic `[[immoskill]]` (status: draft) angelegt
  - Cross-Link von `[[immolizer]]` nach `[[immoskill]]` ergänzt — beide adressieren denselben Eigentümer, anderer Job-to-be-done
- `raw/_inbox/` ist jetzt leer
- Index aktualisiert

## [2026-04-09] prioritize | Webdev-Portfolio priorisiert

- `comparisons/webdev-priority-map.md` angelegt
- `mocs/webdev-overview.md` um Core, Secondary, Internal Infrastructure und Archive/Legacy erweitert
- `agent-mad/project-radar.md` von Domain-Sicht auf Bucket-Sicht umgestellt
- Core-Fokus aktuell auf Immolizer, TeamChef und WORKxs gesetzt

## [2026-04-10] ingest | raw/_inbox (11 Dateien) abgearbeitet

Zweite Ingest-Welle. `raw/_inbox/` ist jetzt wieder leer.

Verteilt nach `raw/`:
- `Fußballvereine in den EU.md` → `raw/articles/eu-football-clubs-research.md`
- `Immobilien-Kategorien.md` → `raw/notes/immobilien-kategorien.md`
- `Immolizer - ImmoScout Datenintegration.md` → `raw/articles/immoscout-datenintegration.md`
- `Immolizer - Immobilienplattformen in EU.md` → `raw/articles/eu-immobilienplattformen-deep.md`
- `Open-Source Personal-Finance- und Haushaltsbudget.md` → `raw/articles/open-source-finance-apps.md`
- `PRD – Immolizer.md` → `raw/notes/immolizer-prd.md`
- `SKILLER - ⚽ MVP Teamchef.md` → `raw/notes/teamchef-mvp-dialog.md`
- `Technische Umsetzung von JMail.md` → `raw/notes/jmail-umsetzung-dialog.md`
- `feature_entwicklung_grundgerust.md` → `raw/notes/feature-grundgerust-template.md`
- `icon-generator-prompt.md` → `raw/notes/icon-generator-prompt.md`
- `wc2026_matches_dewiki.json` → gelöscht (byte-identisches Duplikat von `raw/data/wc2026_matches_dewiki.json`)

Neue Source Notes:
- `[[immolizer-prd]]`, `[[immobilien-kategorien]]`, `[[immoscout-datenintegration-source]]`, `[[eu-immobilienplattformen-deep]]`, `[[open-source-finance-apps]]`, `[[eu-football-clubs-research]]`, `[[teamchef-mvp-dialog]]`, `[[jmail-umsetzung-dialog]]`

Wiki-Seiten:
- `[[immolizer]]` erweitert um PRD-Kern, Datenmodell-Referenz auf Feldkatalog, ImmoScout-Integration, Marktumfeld und UX-Referenzen
- `[[teamchef]]` erweitert um MVP-Plan (WordPress + CFF), Datenmodell-Entitäten und EU-Vereinsgrößenordnung
- Neu: Topic `[[open-source-finance-ux]]` als UX-Referenz-Bündel für Immolizer
- Neu: Entity `[[jmail-world]]` als externe Architektur-Referenz (kein eigenes Projekt)

Patterns (`agent-mad/patterns/`):
- `feature-grundgeruest.md` — verbindliche 10-Abschnitt-Vorlage für Feature-Entwicklung
- `icon-generator-prompt.md` — isometrischer 3D-Icon-Style als Prompt-Preset

Index aktualisiert.

## [2026-04-10] meta | Workflow-Regeln: Auto-Commit nach Inbox + Dedup-Check + raw/ in Git

- `CLAUDE.md` und `AGENTS.md` ergänzt:
  - Pflicht-Commit + Push nach jedem Aufräumen von `raw/_inbox/` (Commit-Typ `ingest`, atomarer Schritt wegen Multi-PC-Sync)
  - Dedup-Check vor jedem Verschieben aus `raw/_inbox/`: Grep nach `source:`-URL und Titel-Slug, Behandlung für identisch / aktualisiert / Konflikt
  - `raw/` wird vollständig mit committet (Provenance + Multi-PC-Sync + Re-Processing); Binaries erst bei realem Repo-Bloat ausschließen
- Grund: `raw/_inbox/`-Leerung darf nicht halb im Working Tree liegen bleiben, und Duplikate müssen beim Ingest erkannt werden statt sich im Vault anzusammeln
