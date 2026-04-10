---
title: "openclaw Decisions — Überblick"
type: topic
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, decisions]
confidence: high
---

# openclaw Decisions

Entscheidungen rund um openclaw-Architektur, Config und Agent-Design.
Append-only — Entscheidungen nicht umschreiben, sondern neue nachschieben.

## Entscheidungen

### 2026-02-13 — Multi-Agent-Struktur, Git init
Entscheidung, den Stack als Multi-Agent-System mit eigenem Git-Repo aufzubauen.

### 2026-02-21 — Cody, James, Clara erstellt
Drei Spezialagents (Coder, Researcher, Lawyer) als initiales Setup.

### 2026-02-22 — LLM-Zuweisung + Memory-Umbau
- LLM-Zuweisung pro Agent finalisiert
- `MEMORY.md` auf lean umgestellt
- `BRAIN.md` als deep knowledge base eingeführt, nur on-demand via `memory_search`

### 2026-04-10 — openclaw-Doku nach Brain4Mad absorbiert
Dokumentation (nicht Runtime) wird ab jetzt in `Brain4Mad/agent-mad/openclaw/`
gepflegt. `.openclaw/*.md` bleiben unangetastet als Live-Runtime.
**Why:** Trennung von Runtime (SSoT bleibt `.openclaw/`) und verdichteter Doku, um
Wissen multi-PC-synchron und in Git-Historie verfügbar zu haben.
**How to apply:** Bei konzeptionellen Änderungen Doku hier nachziehen, Runtime-Werte
nie hier spiegeln.
