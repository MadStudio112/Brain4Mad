# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Was dieses Repo ist

Brain4Mad ist **kein Code-Projekt**, sondern ein persistentes LLM-Wiki als Obsidian-Vault. Inhalt = Markdown-Seiten mit YAML-Frontmatter und Wikilinks (`[[…]]`). Es gibt keinen Build, keine Tests, keinen Lint — gearbeitet wird direkt an `.md`-Dateien. Sprache der Inhalte: **Deutsch**.

Teil von MadStudio112 → `git pull` vor der Arbeit, Änderungen sofort pushen (siehe `C:\Users\Mad\CLAUDE.md`).

## Schichten-Modell (wichtig für jeden Edit)

Das Wiki hat drei klar getrennte Schichten. Änderungen nie über die Schichtgrenze hinweg vermischen:

1. **`raw/`** — unveränderte Rohquellen (Artikel, Transcripts, Notes, Bilder, Daten). **Nie umschreiben.** Neue Quellen landen in `raw/_inbox/` und werden von dort in die passenden Unterordner (`articles/`, `documents/`, `transcripts/`, `notes/`, `images/`, `data/`) verteilt.
2. **`sources/`** — Source Notes: strukturierte Zusammenfassungen einzelner Rohquellen. Brücke zwischen `raw/` und Wiki.
3. **Wiki-Ordner** (`entities/`, `concepts/`, `topics/`, `comparisons/`, `synthesis/`, `questions/`, `timelines/`, `decisions/`, `mocs/`) — verdichtetes, verlinktes Wissen. Hier werden Erkenntnisse aus mehreren Quellen integriert, **nicht** dupliziert.

`projects/` = aktive Vorhaben als `projects/<domain>/<projekt>/` mit `overview.md`, `notes.md`, `decisions.md`, `tasks.md`.

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

1. Erst relevante Quellen in `raw/`/`sources/` lesen, dann Wiki ändern.
2. `raw/_inbox/` möglichst leer halten — neue Rohquellen sofort einsortieren.
3. Neue Erkenntnisse **in bestehende Seiten integrieren** statt Duplikate anzulegen. Widersprüche explizit notieren (nicht stillschweigend überschreiben).
4. Nach relevanten neuen/geänderten Seiten: `index.md` aktualisieren (globaler Katalog).
5. `log.md` ist **append-only** — jeder nennenswerte Change bekommt dort einen Eintrag mit Datum, Art (`init` / `ingest` / `restructure` / `openclaw` / …) und Kurzbegründung.
6. Wikilinks (`[[seitenname]]`) konsistent pflegen, YAML-Frontmatter kurz halten.
7. **Nach jedem Aufräumen von `raw/_inbox/` zwingend `git commit` + `git push`.** Inbox-Leerung ist ein atomarer Schritt und darf nicht halb im Working Tree liegen bleiben — sonst bricht der Multi-PC-Sync (siehe `C:\Users\Mad\CLAUDE.md`). Commit-Typ: `ingest`.
8. **Dedup-Check beim Verarbeiten jeder Inbox-Datei** — bevor eine `raw/_inbox/*`-Datei in ihren Ziel-Unterordner verschoben wird, prüfen ob inhaltlich schon vorhanden:
   - Match nach `source:`-URL im Frontmatter (Grep über `raw/`)
   - Match nach Titel-Slug / ähnlichem Dateinamen in `raw/articles|notes|transcripts|documents/`
   - Bei Treffer Inhalt vergleichen:
     - **Identisch** → neue Datei löschen, `log.md`-Eintrag Typ `dedup` mit Pfad der behaltenen Version
     - **Aktualisierte Version derselben Quelle** → alte zu `<slug>-v1.md` (oder `-YYYY-MM-DD`) umbenennen, neue als aktuelle Version ablegen, in der zugehörigen `sources/`-Note beide Versionen verlinken
     - **Echter Konflikt** (gleiche Quelle, widersprüchlicher Inhalt) → beide behalten, Widerspruch in `sources/` explizit notieren

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
type: topic | entity | concept | comparison | synthesis | question | timeline | source
status: active | draft | archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: [...]
confidence: high | medium | low
---
```

`status: draft` = halbfertig, noch nicht verdichtet. Gehört an den **Zielort**, nicht in einen Staging-Ordner.

## .pen-Dateien

Falls `.pen`-Dateien auftauchen: **nur** über die `pencil` MCP-Tools lesen/schreiben (`batch_get`, `batch_design`, …) — **nie** mit `Read`/`Grep`, der Inhalt ist verschlüsselt.

## Schreibstil

Prägnant, konkret, source-grounded. Unsicherheit/Status/Confidence sichtbar machen. Kein Fülltext, keine Chat-Prosa.
