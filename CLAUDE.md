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
