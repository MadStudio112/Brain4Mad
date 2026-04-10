---
title: "openclaw Skills — Überblick"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, skills]
confidence: medium
---

# openclaw Skills

Modulare Agent-Anweisungen mit `SKILL.md`.

## Speicherorte

| Ort | Scope |
|---|---|
| `C:\Users\Mad\.codex\skills\...` | Global verfügbare Skills |
| `C:\Users\Mad\.openclaw\skills\` | openclaw-workspace-spezifisch |
| `C:\Users\Mad\.openclaw\workspace\skills\` | projektbezogen im Workspace |

## Prinzip (Lazy Loading)

Ein Skill wird **nur geladen, wenn die Aufgabe ihn wirklich braucht**. Kontext schlank
halten. Keine Monster-`AGENTS.md` bauen, stattdessen Funktionalität in Skills schneiden.

## Typische Skill-Kandidaten (aus README-hacks)

- GitHub-Workflow
- PR-Review
- Release-Prozess
- Deployment
- Supabase-Migrationen
- Legal-Dossier-Workflows
- CSV/Seeder-Importe

## Zu dokumentieren

- Vollständige Liste der aktuell existierenden Skills (pro Agent und global)
- Welche Skills von welchem Agent genutzt werden
- Lade-Trigger (automatisch vs. manuell)
