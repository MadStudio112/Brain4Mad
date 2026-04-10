---
title: "openclaw Cron — Überblick"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, cron]
confidence: low
---

# openclaw Cron

Ort: `C:\Users\Mad\.openclaw\cron\`

## Prinzipien

- **Minimal halten** — weniger oft, bündeln statt parallelisieren
- **Isoliert ausführen** — jeder Job eigene Session, kein Main-Thread-Druck
- **Nie** luxuriös auf Premium-Modell ohne Grund

## Zu dokumentieren

- Aktive Cron-Jobs mit Schedule, Zweck, Modell
- Abhängigkeiten (welcher Job nutzt welche APIs/Skills)
- Log-Ablage und Fehler-Kanal
