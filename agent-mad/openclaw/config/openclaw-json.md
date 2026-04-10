---
title: "openclaw.json"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, config]
confidence: low
---

# openclaw.json

Haupt-Konfigurationsdatei unter `C:\Users\Mad\.openclaw\openclaw.json` (~12 KB).

## Zweck

Zentrale Laufzeit-Config des openclaw-Stacks. Wird beim Start gelesen und definiert
Agents, Tools, Modelle, Routing, Skills, Flows, Cron, Approvals.

## Struktur

_TODO: Felder und Sektionen dokumentieren, sobald konkrete Änderungen anstehen.
Live-Wahrheit immer aus der Datei selbst lesen, nicht hier spiegeln._

## Änderungen

- Backup-Kette: `openclaw.json.bak`, `.bak.1` … `.bak.4`
- Bei Konflikt: `openclaw.json.clobbered.<timestamp>` (siehe [[../troubleshooting/overview]])

## Offene Fragen

- Welche Felder sind stabile SSoT, welche werden vom Runtime überschrieben?
- Wie kollidieren `openclaw.json` und `agents/main/AGENTS.md` bei Widersprüchen?
