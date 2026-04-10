---
title: "openclaw Agents — Überblick"
type: topic
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, agents]
confidence: medium
---

# openclaw Agents

Agent-Struktur unter `C:\Users\Mad\.openclaw\agents\`.

## Hierarchie

- **Main-Agent** (`agents/main/`) — primäre SSoT, Router, Session-Start-Regeln
- **Spezialagents**:
  - **Cody** (Coder) — [[cody]]
  - **James** (Researcher) — [[james]]
  - **Clara** (Lawyer) — [[clara]]

## Jeder Agent hat

Standard-Dateien pro Agent-Ordner: `AGENTS.md`, `SOUL.md`, `IDENTITY.md`, `TOOLS.md`,
ggf. weitere Persona-Dateien. Main-Agent hat zusätzlich `MEMORY.md` und ein
`memory/`-Tageslog.

## Änderungs-Regel

- Änderungen zuerst in `agents/main/` oder im jeweiligen Agent-Ordner.
- Root-`*.md` in `.openclaw/` sind nur Router-Stubs und dürfen überschrieben werden.
- Keine doppelte Pflege derselben Regel an mehreren Orten.
