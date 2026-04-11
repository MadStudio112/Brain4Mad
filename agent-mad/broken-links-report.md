---
title: "Broken Links Report"
type: meta
status: active
generated: 2026-04-11
tags: [meta, maintenance]
confidence: high
---

# Broken Links Report

Zuletzt geprüft: **2026-04-11** nach Projekt-First-Restructure (Commits 1–9).

## Status

**Keine echten broken links** in der Wiki-Struktur.

Gefundene "Treffer" beim Scan sind ausnahmslos Placeholder-Text aus Dokumentationsdateien:

| Datei | Link | Typ |
|---|---|---|
| `CLAUDE.md` | `[[seitenname]]`, `[[neuer-name]]`, `[[...]]` | Beispiel in Doku-Text |
| `AGENTS.md` | `[[...]]` | Beispiel in Doku-Text |
| `log.md` | `[[Projektname]]` | Template-Beispiel in altem Log-Eintrag |

## Aliases-Abdeckung

Alle umbenannten Dateien der Restructure tragen `aliases:` im Frontmatter — bestehende Wikilinks funktionieren weiter:

- `[[workxs]]` → `projects/webdev/workxs/overview.md`
- `[[immolizer]]` / `[[Immolizer]]` → `projects/webdev/immolizer/overview.md`
- `[[teamchef]]` / `[[TeamChef]]` → `projects/webdev/teamchef/overview.md`
- `[[immolizer-open-questions]]` → `projects/webdev/immolizer/questions.md`
- `[[teamchef-open-questions]]` → `projects/webdev/teamchef/questions.md`
- `[[workxs-open-questions]]` → `projects/webdev/workxs/questions.md`
- `[[immolizer-prd]]` → `projects/webdev/immolizer/brief.md`
- `[[immolizer-source-migration]]` → `projects/webdev/immolizer/_source-migration.md`
- `[[immolizer-raw-structure]]` → `projects/webdev/immolizer/_raw-structure.md`
- `[[teamchef-source-migration]]` → `projects/webdev/teamchef/_source-migration.md`
- `[[teamchef-raw-structure]]` → `projects/webdev/teamchef/_raw-structure.md`
- `[[workxs-competitor-landscape]]` → `projects/webdev/workxs/competitors/_overview.md`
- `[[warren-project]]` → `projects/webdev/warren/overview.md`
- `[[jmail-world]]` → `projects/webdev/jmail/overview.md`
- `[[webdev-overview]]` → `projects/webdev/_overview.md`
- `[[home]]` → `overview.md`

## Nächste Prüfung

Nach nächstem größerem Restructure oder massenhafter Dateiumbenennung neu ausführen.
