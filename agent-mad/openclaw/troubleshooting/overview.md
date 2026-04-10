---
title: "openclaw Troubleshooting — Überblick"
type: topic
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, troubleshooting]
confidence: medium
---

# openclaw Troubleshooting

Bekannte Probleme und Fixes rund um openclaw.

## Bekannte Probleme

### Clobbered `openclaw.json`

**Symptom:** Im Runtime-Ordner tauchen `openclaw.json.clobbered.<timestamp>`-Dateien auf.

**Ursache:** Parallele Schreibvorgänge kollidieren — mehrere Prozesse/Agents schreiben
gleichzeitig, der Verlierer wird als `.clobbered` abgelegt.

**Fix:** Noch offen. Kandidaten:
- Write-Lock oder atomarer Rename-Commit
- Single-Writer-Konvention für `openclaw.json`
- Backup-Kette (`.bak`, `.bak.1`…) ist bereits vorhanden

**Beobachtung 2026-04-08:** Mehrere Clobber-Events innerhalb weniger Minuten
(15:00:20–15:01:10) — deutet auf einen Event-Loop oder Race hin.

### Notion API-Version Falle

**Symptom:** Property-Bugs bei Notion-Operationen.

**Ursache:** Notion API-Version `2025-09-03` hat Bugs bei Properties.

**Fix:** Version `2022-06-28` verwenden.

### Cleanup-Risiko-Kandidaten

Folgende Ordner **nie** blind löschen — siehe BRAIN.md / DOSSIER.md für Details:
- `cache/` (Rebuild nötig)
- `media/` (lokale Medienartefakte)
- `memory/*.sqlite` (Agent-DB, Verlaufsdaten)
- `.claude/` (Tool-/Editor-Settings)
- `workspace/.clawhub/` (Lock/Workspace-Metadaten)
- `skills/`, `workspace/skills/` (Custom-Skills)

Bei aggressivem Cleanup: erst Backup, dann in Reihenfolge
`cache` → `workspace/.clawhub` → `media` → `.claude`. `memory/*.sqlite` und
`skills/*` nur zuletzt und nur bei bestätigter Nichtnutzung.
