---
title: "models.json"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, config, models]
confidence: low
---

# models.json

Modell-Registry unter `C:\Users\Mad\.openclaw\models.json` (~1.8 KB).

## Zweck

Definiert verfügbare LLMs und ihr Routing. Wird vom Main-Agent und Subagents
herangezogen, um pro Aufgabe das passende Modell zu wählen.

## Routing-Prinzip (aus README-hacks und BRAIN.md abgeleitet)

- **Opus** für Denken/Entscheiden/Architektur/harte Analyse
- **Günstigere Modelle** für Muskel-Tasks: Codex fürs Coden, Minimax für Research,
  Qwen für Creative Writing
- **Default-Modell günstig** halten, starkes Modell nur gezielt einsetzen
- **Cron-Jobs niemals** luxuriös auf Premium-Modell ohne Grund

## Sync

Es existiert `sync-models.ps1` im Runtime-Ordner für Modell-Sync. Zweck und Trigger
sind noch zu dokumentieren.

## Offene Fragen

- Welche Modelle sind aktuell registriert? (live aus `models.json` lesen)
- Wie wird das Routing aktuell implementiert — per Config oder per Agent-Prompt?
