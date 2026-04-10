---
title: "Überblick"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-09
tags: [meta, overview]
confidence: high
---

# Überblick

Brain4Mad ist ein persistentes, von LLMs gepflegtes Wissenssystem.

## Zweck

- Wissen dauerhaft speichern statt es immer neu herzuleiten
- Quellen in kompilierte, verlinkte Wissensseiten überführen
- Widersprüche, Unsicherheiten und offene Fragen sichtbar machen
- Recherchen, Entscheidungen und laufende Arbeit in einem gemeinsamen Gehirn bündeln

## Schichten

| Ebene | Rolle |
|---|---|
| `raw/` | Unveränderte Rohquellen, Attachments, Imports |
| `sources/` | Quellnotizen und strukturierte Zusammenfassungen |
| Wiki-Ordner | Verdichtetes, verlinktes Wissen |

## Kernstruktur

| Verzeichnis | Inhalt |
|---|---|
| `raw/` | Rohmaterial als Source of Truth (Eingang: `raw/_inbox/`) |
| `projects/` | Aktive Vorhaben und laufende Arbeit |
| `decisions/` | Entscheidungen mit Kontext und Begründung |
| `mocs/` | Maps of Content, Navigation, Themen-Hubs |
| `sources/` | Dokumentation einzelner Quellen |
| `entities/` | Personen, Firmen, Produkte, Orte, Systeme |
| `concepts/` | Begriffe, Modelle, Methoden, Ideen |
| `topics/` | Thematische Zusammenfassungen und Dossiers |
| `comparisons/` | Strukturierte Vergleiche |
| `synthesis/` | Übergreifende Einordnungen und Meta-Analysen |
| `questions/` | Offene Fragen, Lücken, Unsicherheiten |
| `timelines/` | Chronologien und Ereignisketten |

## Arbeitsweise

- Rohquellen bleiben unverändert in `raw/`
- Das Wiki wird inkrementell gepflegt und verdichtet
- Antworten, Analysen und Vergleiche können als neue Seiten zurück ins Wiki fließen
- `index.md` dient als globaler Katalog, `log.md` als Verlauf

---

Siehe auch: [[index]] | [[log]]
