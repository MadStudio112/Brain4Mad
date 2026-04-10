---
title: "Feature-Grundgerüst"
type: pattern
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [pattern, feature, template, product]
confidence: high
---

# Feature-Grundgerüst

Verbindliche Vorlage für die Entwicklung neuer Features — wird bei jedem Feature vollständig ausgefüllt und dient als Basis für Design, Entwicklung und QA.

Rohquelle: `raw/notes/feature-grundgerust-template.md`

## Struktur (10 Abschnitte)

1. **Ziel des Features** — Problem/Nutzen, Business-Ziel, Erfolgskriterien (KPIs)
2. **User Flow** — Entry Point, Happy Path, Alternative Flows, Exit Points
3. **User Story / User Stories** — Primäre Story (`Als … möchte ich …, um …`), Akzeptanzkriterien, Sekundäre Stories
4. **Anforderungen an Eingaben und Daten** — User-Input, Systemdaten, vereinfachtes Datenmodell
5. **Berechnung / Logik** — Trigger, Formel/Regelwerk, Ergebnis-Typen
6. **UI-Komponenten** — Eingabefelder, Selektoren, Ergebnisanzeige, Visualisierungen
7. **Nicht-Ziele / Out of Scope**
8. **Abhängigkeiten & Risiken** — technisch, Datenqualität, Performance
9. **Offene Fragen**
10. **Übergabe an Entwicklung** — Status (Draft/Ready/In Umsetzung), Owner, Datum

## Verwendung

- Bei jedem neuen Feature-Entwurf **vollständig** ausfüllen, nicht selektiv
- Gilt für [[immolizer]], [[teamchef]], [[workxs]] und alle weiteren Produktprojekte
- Status im Frontmatter/Abschnitt 10 hält Reife sichtbar
