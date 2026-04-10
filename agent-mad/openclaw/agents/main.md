---
title: "Main-Agent"
type: entity
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, agent, main]
confidence: medium
---

# Main-Agent

Ort: `C:\Users\Mad\.openclaw\agents\main\`

## Rolle

Router und primäre SSoT des openclaw-Stacks. Bei Konflikten mit Root-`*.md` in
`.openclaw/` gewinnt `agents/main/`.

## Dateien (laut DOSSIER)

| Datei | Zweck |
|---|---|
| `AGENTS.md` | Session-Start-Regeln, operative Policies, Routing |
| `SOUL.md` | Stil/Verhalten |
| `IDENTITY.md` | Identität des Agents |
| `USER.md` | User-Profil (Mad) |
| `ROLE.md` | Rollenbeschreibung |
| `TOOLS.md` | Verfügbare Tools |
| `CAPABILITIES.md` | Capabilities-Manifest |
| `MEMORY.md` | Lean Routing-Sheet, immer geladen |
| `HEARTBEAT.md` | Heartbeat-Logik für Idle-Checks |
| `memory/YYYY-MM-DD.md` | Tageslog |

## Prinzipien (aus README-hacks)

- Global-Dateien minimal halten (AGENTS = Routing, SOUL = Stil, MEMORY = nur Dauerhaftes)
- Projektwissen in Projektdateien, nicht in globale Persona-Dateien
- Skills statt Monster-AGENTS.md
- Heartbeats + Idle-Checks laden Dateien nur bei Bedarf
- Subagents werden erzeugt, erledigen, melden, Kontext endet
