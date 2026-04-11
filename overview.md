---
title: "Überblick"
type: meta
status: active
created: 2026-04-09
updated: 2026-04-11
tags: [meta, overview]
confidence: high
aliases: [home]
---

# Brain4Mad — Überblick

Persistentes, von LLMs gepflegtes Wissenssystem für aktive Projekte und Recherchen.

## Zweck

- Wissen dauerhaft speichern statt es immer neu herzuleiten
- Quellen in kompilierte, verlinkte Projektseiten überführen
- Widersprüche, Unsicherheiten und offene Fragen sichtbar machen

## Struktur

| Verzeichnis | Inhalt |
|---|---|
| `raw/` | Unveränderte Rohquellen (Eingang: `raw/_inbox/`) |
| `projects/webdev/` | Web- und Software-Projekte |
| `projects/research/` | Themen ohne Code |
| `projects/personal/` | Persönliche Projekte |
| `reference/` | Echtes Cross-Project-Wissen (klein, wächst bei Bedarf) |
| `agent-mad/` | Arbeitsgedächtnis des Agents |

## Schnellzugriff

- [[index]] — globaler Katalog aller Seiten
- [[log]] — Änderungsprotokoll
- [[projects/webdev/_overview|Webdev-Projekte]] — Portfolio-Übersicht

## Webdev-Projekte (aktiv)

| Projekt | Status |
|---|---|
| [[immolizer/overview\|Immolizer]] | aktiv |
| [[teamchef/overview\|TeamChef]] | aktiv |
| [[workxs/overview\|WORKxs]] | aktiv |
| [[warren/overview\|Warren]] | aktiv |
| [[jmail/overview\|JMail]] | aktiv |

Alle Projekte: [[projects/webdev/_overview|Webdev Overview]]

## Arbeitsweise

- Rohquellen landen in `raw/_inbox/`, werden in `raw/` einsortiert
- Wissen wird als verlinktes Markdown in `projects/` verdichtet
- `index.md` = globaler Katalog, `log.md` = Verlauf
