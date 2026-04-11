---
title: "Immolizer PRD (Kurzfassung)"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [immolizer, prd, proptech]
confidence: high
aliases: [immolizer-prd]
---

# Immolizer PRD (Kurzfassung)

Quelle: `raw/notes/immolizer-prd.md`

## Kernaussagen

- **Onboarding**: User erfasst 5–10 harte Fakten zur Immobilie (Fläche, Zimmer, Baujahr, Preis, Energieklasse …).
- **Dashboard**: Nach Eingabe sieht der User eine Vergleichsansicht mit Durchschnitt, Minimum und Maximum ähnlicher Objekte.
- **Widgets**: Pro Fakt ein eigenes Widget (z. B. Preis/m², Energiekennzahl), das individuell verglichen wird.
- **Monetarisierung**: Freies Einsteiger-Modell, tiefere Analysen oder erweiterte Vergleiche kostenpflichtig.

## Einordnung

Das PRD ist der knappste bisher vorliegende Produkt-Scope-Text zu [[immolizer]]. Er bestätigt den bisherigen MVP-Kern (Erfassung → Typenschein → Vergleich) und legt die Widget-Logik als zentrales UI-Pattern fest.

## Offen

- Datenherkunft der Vergleichswerte (ImmoScout-API? öffentliche Quellen? User-Pool?) — siehe [[immoscout-datenintegration-source]]
- Widget-Schnitt und Scoring-Logik
