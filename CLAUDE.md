# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Was dieses Repo ist

Brain4Mad ist **kein Code-Projekt**, sondern ein persistentes LLM-Wiki als Obsidian-Vault. Inhalt = Markdown-Seiten mit YAML-Frontmatter und Wikilinks (`[[…]]`). Es gibt keinen Build, keine Tests, keinen Lint — gearbeitet wird direkt an `.md`-Dateien. Sprache der Inhalte: **Deutsch**.

Teil von MadStudio112 → `git pull` vor der Arbeit, Änderungen sofort pushen (siehe `C:\Users\Mad\CLAUDE.md`).

## Schichten-Modell (wichtig für jeden Edit)

Das Wiki hat zwei klar getrennte Schichten. Änderungen nie über die Schichtgrenze hinweg vermischen:

1. **`raw/`** — unveränderte Rohquellen (Artikel, Transcripts, Notes, Bilder, Daten). **Nie umschreiben.** Neue Quellen landen in `raw/_inbox/` und werden von dort in die passenden Unterordner (`articles/`, `documents/`, `transcripts/`, `notes/`, `images/`, `data/`) verteilt.
2. **Wiki-Ordner** — verdichtetes, verlinktes Wissen, fraktal nach Projekten organisiert:
   - `projects/<domain>/<projekt>/` — Hauptarbeitsbereich. Pro Projekt: `overview.md`, optional `notes.md`, `questions.md`, `brief.md`, `decisions.md`, `_raw-structure.md`. **Kein `tasks.md`.**
   - `reference/` — echtes Cross-Project-Wissen (klein; nur promoten, wenn Inhalt aus ≥2 Projekten gebraucht wird)
   - `agent-mad/` — Arbeitsgedächtnis des Agents
   - Root: `index.md`, `log.md`, `overview.md`

**Projekt-Struktur:** `projects/webdev/` für Web-/Software-Projekte, `projects/research/` für Themen ohne Code, `projects/personal/` für private Themen. Projektfamilien bekommen eine `_familienname.md`-Klammer-Datei im Parent-Ordner (z.B. `projects/webdev/_immolizer-family.md`).

**Fraktaler Ansatz:** Alles zu einem Projekt gehört in den Projektordner. Erst wenn Inhalt wirklich für ≥2 Projekte gebraucht wird, zieht er nach `reference/` um. Wikilinks funktionieren über Ordner hinweg — Querverweise sind kostenlos.

**Kein `inbox/`** auf Wiki-Ebene. Für rohe Quellen-Captures gibt es `raw/_inbox/`. Halbfertige Wiki-Seiten bekommen direkt am Zielort `status: draft` im Frontmatter — kein separater Staging-Ordner.

## `agent-mad/` — Arbeitsbereich des Agents

Zwei Rollen, klar getrennt:

1. **Root-Ebene** = Wiki-Arbeitsgedächtnis: `working-context.md`, `project-radar.md`, `decision-rules.md`, `mistakes.md`, `daily/`, `patterns/`.
2. **`agent-mad/openclaw/`** = openclaw-Wissensbasis. Dokumentiertes Wissen über den openclaw-Agent-Stack unter `C:\Users\Mad\.openclaw\` — Architektur, Agents, Skills, Flows, Config, Entscheidungen, Troubleshooting. **Einstieg: `agent-mad/openclaw/overview.md`**.

### openclaw — Runtime vs. Doku

- **Runtime SSoT:** `C:\Users\Mad\.openclaw\` (live Config, Credentials, Logs, Agents). Änderungen an laufender Config **immer dort**. Primäre Agent-SSoT ist `C:\Users\Mad\.openclaw\agents\main\` — bei Konflikten mit Root-`*.md` gewinnt `agents/main`.
- **Doku:** `agent-mad/openclaw/`. Verdichtete, erklärte Sicht auf den Stack. **Nie Live-Dumps spiegeln.** Live-Werte immer aus `.openclaw/` lesen, hier nur Struktur und Zweck dokumentieren.
- **Update-Modus:** Pull-basiert — bei konzeptionellen Änderungen (neuer Agent, neue Skill, Architekturumbau) Doku in `agent-mad/openclaw/` nachziehen. Keine automatische Spiegelung.
- **`.openclaw/*.md`** (BRAIN, DOSSIER, IDENTITY, SOUL, ROLE, USER, TOOLS, MEMORY, CAPABILITIES, HEARTBEAT, README, README-hacks) bleiben **unangetastet**.

### Secrets-Blocklist (kritisch)

Brain4Mad ist git-synchronisiert. **Niemals** in `agent-mad/` oder sonstwo in Brain4Mad: `.env`-Werte, API-Keys, Tokens, OAuth-Credentials, Inhalte aus `.openclaw/credentials/`, `exec-approvals.json`, Logs mit PII, SQLite-Dumps aus `.openclaw/memory/`. Erlaubt: **nur** Variablennamen, Config-Struktur, Zweck-Erklärungen. Details: `agent-mad/README.md`.

## Pflicht-Workflow bei Änderungen

1. Erst relevante Quellen in `raw/` lesen, dann Wiki ändern.
2. `raw/_inbox/` möglichst leer halten — neue Rohquellen sofort einsortieren.
3. Neue Erkenntnisse **in bestehende Projektseiten integrieren** statt Duplikate anzulegen. Widersprüche explizit notieren (nicht stillschweigend überschreiben).
4. Nach relevanten neuen/geänderten Seiten: `index.md` aktualisieren (globaler Katalog).
5. `log.md` ist **append-only** — jeder nennenswerte Change bekommt dort einen Eintrag mit Datum, Art (`init` / `ingest` / `restructure` / `openclaw` / …) und Kurzbegründung.
6. Wikilinks (`[[seitenname]]`) konsistent pflegen, YAML-Frontmatter kurz halten. **Kein Inline-Tag** (`#tag`) im Fließtext — nur `tags: [...]` im Frontmatter.
7. **Nach jedem Aufräumen von `raw/_inbox/` zwingend `git commit` + `git push`.** Inbox-Leerung ist ein atomarer Schritt und darf nicht halb im Working Tree liegen bleiben — sonst bricht der Multi-PC-Sync (siehe `C:\Users\Mad\CLAUDE.md`). Commit-Typ: `ingest`.
8. **Dedup-Check beim Verarbeiten jeder Inbox-Datei** — bevor eine `raw/_inbox/*`-Datei in ihren Ziel-Unterordner verschoben wird, prüfen ob inhaltlich schon vorhanden:
   - Match nach `source:`-URL im Frontmatter (Grep über `raw/`)
   - Match nach Titel-Slug / ähnlichem Dateinamen in `raw/articles|notes|transcripts|documents/`
   - Bei Treffer Inhalt vergleichen:
     - **Identisch** → neue Datei löschen, `log.md`-Eintrag Typ `dedup` mit Pfad der behaltenen Version
     - **Aktualisierte Version derselben Quelle** → alte zu `<slug>-v1.md` (oder `-YYYY-MM-DD`) umbenennen, neue als aktuelle Version ablegen, in der zugehörigen Projektseite beide Versionen verlinken
     - **Echter Konflikt** (gleiche Quelle, widersprüchlicher Inhalt) → beide behalten, Widerspruch in Projektseite explizit notieren

## `raw/` und Git

`raw/` wird **vollständig mit committet** — inklusive aller Unterordner (`articles/`, `documents/`, `transcripts/`, `notes/`, `images/`, `data/`). Begründung:

- **Provenance:** `sources/`-Notes sind nur Verdichtungen. Rückprüfung von Aussagen im Wiki braucht die Originalquelle.
- **Multi-PC-Sync:** Brain4Mad wird von mehreren Rechnern bearbeitet. Ohne `raw/` im Repo fehlt auf dem anderen PC der Kontext zum Weiterverarbeiten.
- **Re-Processing:** Aus derselben Rohquelle können später neue Winkel destilliert werden — nur möglich, wenn das Original noch da ist.
- **Größe:** Text/Markdown ist vernachlässigbar. Binaries (große PDFs, Bilder, Daten-Dumps) erst dann per `.gitignore` oder LFS rausziehen, **wenn** das Repo real aufgeht — nicht prophylaktisch.

## Frontmatter-Konvention

Jede Wissensseite beginnt mit YAML-Frontmatter, siehe `overview.md`/`index.md` als Referenz:

```yaml
---
title: "…"
type: project | source | concept | comparison | question | meta
status: active | draft | archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [...]
confidence: high | medium | low
aliases: [alter-basename]         # optional — nur wenn Basename geändert wurde
family: _familienname             # optional — für Projekt-Familien
---
```

`status: draft` = halbfertig, noch nicht verdichtet. Gehört an den **Zielort**, nicht in einen Staging-Ordner.

## Dateinamen-Konvention (Wiki-Ebene)

Gilt für alle `.md` in `projects/`, `reference/`, `agent-mad/` und am Root. **Nicht** für `raw/` — dort ist die Benennung egal, der Ordnerpfad liefert den Kontext.

- **kebab-case, lowercase, ASCII:** `eu-real-estate-platform-landscape.md`. Umlaute transliterieren (`ä/ö/ü` → `ae/oe/ue`, `ß` → `ss`), keine Leerzeichen, keine Sonderzeichen außer `-`.
- **Basename muss ohne Pfad eindeutig sein.** Obsidian zeigt im Graph und in Wikilinks nur den Basename — der Dateiname muss allein lesbar machen, worum es geht.
- **Kein Nummern-Prefix** (`01-`, `02-`). Das ist `raw/notes/`-Stil und gehört nicht ins Wiki.
- **Projekt-Prefix bei Kollisionsgefahr.** Generische Begriffe (`questions`, `overview`, `notes`) werden mit Projektname qualifiziert, wenn sie außerhalb eines Projektordners stehen. Innerhalb eines Projektordners (`projects/webdev/immolizer/overview.md`) ist der Ordner bereits der Namespace — dort bleiben `overview.md`/`notes.md`/`questions.md`/`decisions.md` ohne Prefix.
- **`_`-Prefix für Meta-/Klammer-Dateien** im Ordner: `_immolizer-family.md`, `_teamchef-skiller.md`, `_overview.md`, `_raw-structure.md`, `_source-migration.md`. Obsidian sortiert sie oben, erkennbar als Meta.
- **Typ-Suffix nur zur Disambiguierung, wenn mehrere Seiten denselben Gegenstand aus verschiedenen Winkeln beschreiben.** Ohne Kollision kein Suffix.
- **Versionierung:** archivierte Vorversionen als `<slug>-v1.md`, datumsgebundene Snapshots als `<slug>-YYYY-MM-DD.md`. Siehe auch Dedup-Regel oben.
- **Nicht umbenennen ohne Wikilink-Migration.** Jede Umbenennung erfordert Grep über alle `[[...]]`-Referenzen und Update in `index.md`. Bei Zweifel: neuen Namen als zusätzliche Datei anlegen und alte per Redirect-Stub (`Siehe [[neuer-name]]`) ersetzen, erst dann migrieren.

## .pen-Dateien

Falls `.pen`-Dateien auftauchen: **nur** über die `pencil` MCP-Tools lesen/schreiben (`batch_get`, `batch_design`, …) — **nie** mit `Read`/`Grep`, der Inhalt ist verschlüsselt.

## Schreibstil

Prägnant, konkret, source-grounded. Unsicherheit/Status/Confidence sichtbar machen. Kein Fülltext, keine Chat-Prosa.
