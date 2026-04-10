---
title: "openclaw — Überblick"
type: topic
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, agent, architecture]
confidence: medium
---

# openclaw — Überblick

Agent-Stack unter `C:\Users\Mad\.openclaw\`. Diese Seite ist die verdichtete,
dokumentierte Sicht — **nicht** die Runtime.

## Orte

| Ort | Rolle |
|---|---|
| `C:\Users\Mad\.openclaw\` | **Runtime / Live-State.** Source of Truth für Config, laufende Agents, Logs, Credentials. |
| `C:\Users\Mad\.openclaw\agents\main\` | **Primäre SSoT des Main-Agents.** Bei Konflikten mit Root-`*.md` gewinnt `agents/main`. |
| `Brain4Mad/agent-mad/openclaw/` | **Dokumentation** (dieser Ordner). Wird manuell gepflegt bei konzeptionellen Änderungen. |
| `C:\Users\Mad\Code\ClawX\` | Codebase (aktuell nicht aktiv, ggf. späteres Löschen). |

## Hauptkomponenten

- **Main-Agent** (`agents/main/`) — Router, Session-Start-Regeln, Top-Level-Policies
- **Spezialagents** (`agents/{coder,researcher,lawyer}/`):
  - **Cody** (Coder) — React + TanStack + Hono + Drizzle + Supabase + Vercel/Railway
  - **James** (Researcher) — 6 Säulen: Market, Finance, OSINT, Due Diligence, Tech, Product
  - **Clara** (Lawyer) — AT-Jurisdiktion, RIS/EUR-Lex
- **Skills** (`skills/`, `workspace/skills/`) — modulare, lazy-geladene Anweisungen
- **Subagents** (`subagents/`) — delegierbare Worker
- **Flows** (`flows/`) — mehrstufige Abläufe
- **Cron** (`cron/`) — Zeit-getriggerte Jobs, isoliert ausgeführt
- **Tasks** (`tasks/`) — laufende und vergangene Task-Runs
- **Devices** (`devices/`) — Geräte-Registry
- **Workspace** (`workspace/`) — Projekte, Daten, DBs, Artefakte (**keine** Agent-Personas)

## Wissens-Hierarchie (Memory-Modell)

- `BRAIN.md` = Langzeitwissen, Details, Referenzwissen — **on-demand** via `memory_search`, nicht bei jedem Start
- `agents/main/MEMORY.md` = Lean Routing-Sheet — immer geladen, nur Nötigstes
- `agents/main/memory/YYYY-MM-DD.md` = Tageslog/Kurzzeitkontext

Regel: Alles, was nicht ständig gebraucht wird, gehört aus `MEMORY.md` in `BRAIN.md`
oder ins Tageslog.

## Root-vs-Agents-Main-Regel

Root-`*.md` in `.openclaw/` (IDENTITY, SOUL, ROLE, USER, TOOLS, MEMORY, CAPABILITIES,
HEARTBEAT) sind **Router/Stubs** und zeigen per Markdown-Link auf die echten Dateien in
`agents/main/`. Sie dürfen bei Updates überschrieben werden. Die operative Wahrheit
liegt in `agents/main/`.

## Verweise

- [[agents/overview]] — Agent-Steckbriefe
- [[config/overview]] — Config-Dateien erklärt
- [[skills/overview]] — Skills-System
- [[decisions/overview]] — Config-Entscheidungen
- [[troubleshooting/overview]] — Bekannte Probleme und Fixes
