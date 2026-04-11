---
title: "Änderungsprotokoll"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-11
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
  - `[[eu-real-estate-platforms-western]]` — DE, AT, FR, NL, BE, LU, IE
  - `[[eu-real-estate-platforms-southern]]` — ES, PT, IT, GR, MT, CY
  - `[[eu-real-estate-platforms-northern]]` — SE, DK, FI
  - `[[eu-real-estate-platforms-eastern]]` — PL, CZ, HU, RO, BG, HR, SK, SI, EE, LV, LT
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

## [2026-04-10] ingest | SKILLER/TeamChef-Dialoge aus raw/_inbox eingearbeitet

- Acht Dateien in `raw/_inbox/` im TeamChef/SKILLER-Cluster gesichtet; sechs davon inhaltlich relevant
- Neue Source Note `[[teamchef-skiller-dialogs]]` angelegt
- `[[teamchef]]` erweitert um Fan-Spiel-Charakter, Trainer-Use-Case, digitale Spielerkarten, QCard-UX, nächtliche Auswertungslogik und Datenmodell-Richtung
- `[[teamchef-open-questions]]` um Bewertungsmodell-, Naming-, Speicher- und Scouting-Fragen geschärft
- `[[teamchef-raw-structure]]` auf spätere Dialog-Ingests erweitert
- `SKILLER - Datenbanken in SKILLER.md` als schwache Rohquelle markiert
- `SQL Generator - Box-Muller Normalverteilung SQL.md` nach späterer Befüllung neu bewertet und als technisch relevante Rohquelle eingestuft
- Physisches Verschieben der Rohdateien aus `raw/_inbox/` nach `raw/notes/teamchef/skiller-dialogs/` steht noch aus

## [2026-04-10] ingest | mixed inbox wave (LegalTech, FlatRace, TeamChef)

- Neue Source Note `[[anwaltsliebling-legaltech-brainstorm]]` angelegt
- Neues Topic `[[anwaltsliebling]]` angelegt
- Neue Source Note `[[flatrace-brainstorming]]` angelegt
- `[[immolizer]]` um Naming-Spannung (`Immolizer` / `FlatRace` / `LandingPay` / `Flatpress`) und neue Quelle ergänzt
- Index um LegalTech- und FlatRace-Quellen sowie Topic `[[anwaltsliebling]]` erweitert
- Noch offen: physisches Verschieben der neuen Rohdateien aus `raw/_inbox/` in passende `raw/notes/`-Ziele und anschließender Git-Commit/Push

## [2026-04-11] cleanup | Vault-Audit: kaputte Wikilinks gefixt, Frontmatter nachgezogen, ImmoSkill-Fragen konsolidiert

Audit über alle Nicht-`raw/`-Seiten gelaufen:

**Kaputte Wikilinks (0 verbleibend):**
- Acht Projekt-Topic-Seiten hatten einen "Projektanker"-Selbstlink `[[Projektname]]`, der ins Leere zeigte (AI-HUB, Lawrank, mad-agent, Repo Dashboard, SaaS-360, teamradar, ui_designer, Warren) — auf Pfad-Form `[[mocs/projects/webdev/.../overview|Anzeigename]]` umgestellt
- Forward-Refs aus `[[workxs]]` (5 Stubs) und `[[immoskill]]` (4 Stubs) zeigten auf nie existierende Seiten — ersetzt durch je einen Link auf die konsolidierte Open-Questions-Seite
- `questions/immoskill-open-questions.md` neu angelegt (Positionierung, MVP-Scope, AI-Scope, Datenmodell, Monetarisierung)
- `questions/workxs-open-questions.md` um Monetarisierungs-Sektion erweitert

**Frontmatter nachgezogen:**
- Projekt-Sub-Seiten `mocs/projects/webdev/{immolizer,teamchef}/{notes,tasks}.md` — `overview.md` hatte bereits FM, die Geschwister nicht
- Template `mocs/projects/_template-project/{notes,tasks,decisions}.md`
- Folder-READMEs `decisions/`, `questions/`, `mocs/projects/` — als `type: topic` Navigations-Landings
- Verbleibend ohne FM: nur `CLAUDE.md` und `AGENTS.md` (Instruktionsdateien, keine Wiki-Seiten — bewusst so)

**Index:** `[[immoskill-open-questions]]` ergänzt; Source-Eintrag `[[wc2026-matches-dewiki]]` aus vorherigem Run ebenfalls drin.

## [2026-04-11] restructure | Commit 8/9 — mocs/ aufgelöst, overview.md + _overview.md aktualisiert

- `mocs/webdev-overview.md` → `projects/webdev/_overview.md` (alias `webdev-overview`) — neu geschrieben mit aktueller Projektliste
- `mocs/home.md` → gelöscht, Inhalt in `overview.md` am Root integriert (alias `home`)
- `overview.md` auf neue Struktur (projects/ statt topics/sources/entities/) aktualisiert
- `mocs/projects/_template-project/{overview,notes,decisions}.md` → `projects/_template/` — `tasks.md` weggelassen
- `mocs/projects/README.md`, `decisions/README.md`, `questions/README.md` entfernt
- Alle alten Ordner (topics/, sources/, entities/, concepts/, comparisons/, questions/, decisions/, synthesis/, timelines/, mocs/) sind jetzt leer

## [2026-04-11] restructure | Projekt-First-Migration gestartet — Commit 1: workxs

- `projects/webdev/workxs/` angelegt als erster Pilot der Projekt-First-Struktur
- `topics/workxs.md` + `mocs/.../workxs/overview.md` → `projects/webdev/workxs/overview.md` (merged, alias `workxs`)
- `sources/workxs-brainstorming.md` → `projects/webdev/workxs/workxs-brainstorming.md` (basename stable)
- `questions/workxs-open-questions.md` → `projects/webdev/workxs/questions.md` (alias `workxs-open-questions`)
- `comparisons/workxs-competitor-landscape.md` → `projects/webdev/workxs/competitors/_overview.md` (alias `workxs-competitor-landscape`)
- `entities/{gloat,eightfold-ai,testgorilla,magnetme,switch-job-matching}.md` → `projects/webdev/workxs/competitors/` (basename stable)
- Top-Level-Ordner `projects/`, `reference/` angelegt; `projects/research/`, `projects/personal/` als Platzhalter

## [2026-04-11] restructure | Wiki-Dateinamen-Audit — eu-re-platforms umbenannt

- `comparisons/eu-re-platforms-{eastern,northern,southern,western}.md` → `eu-real-estate-platforms-{...}.md`
- Grund: Abkürzung `re` im Graph-Basename ohne Pfadkontext nicht eindeutig lesbar
- Wikilinks in `index.md`, `log.md`, `sources/eu-real-estate-platforms-research.md`, `topics/eu-real-estate-platform-landscape.md` migriert
- Alle anderen Wiki-Dateien konform mit Naming-Konvention (kebab-case, lowercase, kein Nummern-Prefix, Basename eindeutig)

## [2026-04-11] meta | Dateinamen-Konvention für Wiki-Ebene in CLAUDE.md + AGENTS.md verankert

- Bisher war nur `<slug>-v1.md` für Dedup-Versionen dokumentiert — keine allgemeine Naming-Regel
- Neue Regel in CLAUDE.md (Abschnitt "Dateinamen-Konvention (Wiki-Ebene)") und AGENTS.md gespiegelt
- Kernpunkte: kebab-case/lowercase/ASCII, Basename ohne Pfad eindeutig, kein Nummern-Prefix (`01-` ist `raw/notes/`-Stil), Projekt-Prefix bei Kollisionsgefahr, Typ-Suffix nur zur Disambiguierung, Umbenennung nur mit Wikilink-Migration
- Scope: `sources/`, `topics/`, `entities/`, `concepts/`, `comparisons/`, `synthesis/`, `questions/`, `timelines/`, `decisions/`, `mocs/`, `projects/` — explizit **nicht** `raw/`
- Anlass: Graph-Ansicht zeigt nur Basename — bei zukünftigen Inbox-Durchgängen muss garantiert sein, dass aus Rohquellen erzeugte Wiki-Seiten ohne Pfad lesbar sind

## [2026-04-11] ingest | raw/_inbox geleert — Bau, Immo, Teamchef, Kostenkalkulation

- 48 Dateien aus `raw/_inbox/` in Zielordner verschoben:
  - `raw/documents/bau/` (PDFs + DOC: Bauphysik, Normen, Leitfäden, Regenwasser, OIB, Plandarstellung …)
  - `raw/data/bau/` (XLS/XLSM: Bauphysik-Nachweis, Oberflächen-Berechnung, Versickerung, Berechnung_09)
  - `raw/images/bau/` (JPG: Plandarstellungs-Scans)
  - `raw/documents/bau/einreichung-muster/` (DOC/DOCX: Baubewilligung, Baubeschreibung, Bauanzeige, Ausnahmebewilligung)
  - `raw/images/bau/einreichung-muster/` (JPG/PNG: Ansicht, Schnitt, Grundriss, Aufbauten)
  - `raw/documents/immo/` (PDF: Immo-Energie, Instandhaltung)
  - `raw/images/immo/` (PNG: immowelt_contact_sheet)
  - `raw/data/kostenkalkulation/` (XLSX: Gesamtkosten HTH, K72_uh 2.0)
  - `raw/documents/teamchef/` (PDF: Betradar)
- Leere Inbox-Unterordner entfernt

## [2026-04-11] ingest | Source Note für WM-2026-Spielplan nachgezogen

- `raw/data/wc2026_matches_dewiki.json` (104 Spiele, neues 48-Team-Format, dewiki-Scrape) hatte bisher nur eine beiläufige Erwähnung in `[[eu-football-clubs-research]]` und keine eigene Source Note
- Neue Source Note `[[wc2026-matches-dewiki]]` angelegt: Turnierstruktur (12 Gruppen + Sechzehntelfinale), Zeitraum, Feldschema, Einschränkungen (Platzhalter-Matches, leere Scores, kein Master), Verwendung als Mock-Datensatz für `[[teamchef]]`-UI/Bewertungs-Prototypen
- Index um neuen Source-Eintrag erweitert

## [2026-04-11] restructure | Commit 7/9 — research/ + personal/ migriert

- `topics/aphantasie.md` → `projects/research/aphantasie/overview.md` (alias `aphantasie`)
- `sources/aphantasie-dossier.md` → `projects/research/aphantasie/aphantasie-dossier.md`
- `entities/aprilia-rsv-tuono-1000.md` → `projects/personal/aprilia-rsv-tuono-1000/overview.md` (alias `aprilia-rsv-tuono-1000`)
- `sources/aprilia-rsv-tuono-1000-elektrik.md` → `projects/personal/aprilia-rsv-tuono-1000/aprilia-rsv-tuono-1000-elektrik.md`

## [2026-04-11] restructure | Commit 6/9 — restliche webdev-Projekte migriert

- immoskill, anwaltsliebling, lawrank, mad-agent, repo-dashboard, saas-360, teamradar, ui-designer, ai-hub → je `projects/webdev/<name>/overview.md` (merge aus topics/ + mocs/, aliases gesetzt)
- `sources/immoskill-brainstorming.md`, `sources/anwaltsliebling-legaltech-brainstorm.md` → in Projektordner verschoben
- `questions/immoskill-open-questions.md` → `projects/webdev/immoskill/questions.md` (alias)
- `comparisons/webdev-priority-map.md`, `comparisons/webdev-project-families.md` → `projects/webdev/`
- 9 topics/, 7 mocs/projects/webdev/-Overviews entfernt

## [2026-04-11] restructure | Commit 5/9 — jmail migriert

- `projects/webdev/jmail/overview.md` neu (aus `entities/jmail-world.md`, alias `jmail-world`)
- `sources/jmail-umsetzung-dialog.md` → `projects/webdev/jmail/jmail-umsetzung-dialog.md`
- `entities/jmail-world.md` entfernt

## [2026-04-11] restructure | Commit 4/9 — warren + prediction-markets migriert

- `projects/webdev/warren/overview.md` neu (merge aus `topics/warren-project.md` + `mocs/projects/webdev/warren/overview.md`)
- `topics/polymarket-trading-engine.md`, `topics/open-source-finance-ux.md` → `projects/webdev/warren/`
- `sources/open-source-finance-apps.md`, `sources/polymarket-vs-wettanbieter.md` → `projects/webdev/warren/`
- `concepts/prediction-markets.md` → `projects/webdev/warren/prediction-markets.md`
- `topics/warren-project.md`, `mocs/projects/webdev/warren/overview.md` entfernt

## [2026-04-11] restructure | Commit 3/9 — TeamChef + Skiller-Familie migriert

- `projects/webdev/_teamchef-skiller.md` neu (Bewertungsmodell, QCard-Flow, Normalverteilungs-Logik, Naming-Instabilität)
- `projects/webdev/teamchef/overview.md` neu (merge aus `topics/teamchef.md` + `mocs/projects/webdev/teamchef/overview.md`)
- `projects/webdev/teamchef-v0/overview.md` per git mv aus `mocs/projects/webdev/teamchef-v0/overview.md`
- Sources teamchef-mvp-dialog, teamchef-skiller-dialogs, eu-football-clubs-research, wc2026-matches-dewiki nach `projects/webdev/teamchef/` verschoben
- `sources/teamchef-source-migration.md` → `projects/webdev/teamchef/_source-migration.md` (alias)
- `questions/teamchef-open-questions.md` → `projects/webdev/teamchef/questions.md` (alias)
- `mocs/teamchef-raw-structure.md` → `projects/webdev/teamchef/_raw-structure.md` (alias)
- `topics/teamchef.md`, `mocs/projects/webdev/teamchef/{overview,notes,tasks}.md` entfernt
