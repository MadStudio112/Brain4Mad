---
title: "openclaw Config — Überblick"
type: topic
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, config]
confidence: medium
---

# openclaw Config

Dokumentation der Konfigurationsdateien unter `C:\Users\Mad\.openclaw\`.
**Nur Struktur und Zweck — keine Werte, keine Secrets.**

## Dateien

| Datei | Zweck | Seite |
|---|---|---|
| `openclaw.json` | Haupt-Config des Stacks | [[openclaw-json]] |
| `models.json` | Modell-Registry und Routing | [[models]] |
| `.env` | Secrets, API-Keys, Tokens | [[env]] |
| `.env.example` | Template mit Feldnamen | siehe [[env]] |
| `exec-approvals.json` | Genehmigungslisten für Tool-Calls | (nur Zweck dokumentieren, keine Inhalte) |
| `update-check.json` | Update-Status-Cache | trivial |

## Bearbeitungsregel

- Änderungen **immer live** in `C:\Users\Mad\.openclaw\` vornehmen.
- In diese Doku nur eintragen: **konzeptionelle Struktur**, neue Felder, Routing-Logik,
  Bedeutung — keine Werte.
- Bei größeren Strukturänderungen einen Eintrag in `decisions/` anlegen.

## Backup-Verhalten (beobachtet)

Es existieren `openclaw.json.bak*` und `openclaw.json.clobbered.<timestamp>`-Dateien
im Runtime-Ordner. Clobbered-Dateien entstehen, wenn parallele Schreibvorgänge
kollidieren. → Gehört nach [[../troubleshooting/overview]].
