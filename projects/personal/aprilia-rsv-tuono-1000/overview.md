---
title: "Aprilia RSV Tuono 1000 (2002–2005)"
type: project
status: active
created: 2026-04-10
updated: 2026-04-11
tags: [aprilia, rsv-tuono, motorrad, naked-bike, technik]
confidence: medium
aliases: [aprilia-rsv-tuono-1000]
---

# Aprilia RSV Tuono 1000 (2002–2005)

## Summary

Italienisches Naked-Bike auf Basis der RSV Mille Sportlerplattform, gebaut 2002–2005 mit IE-E2-Magneti-Marelli-Einspritzung. Hier dokumentiert primär als technische Referenz für Kraftstoff- und Sicherheitselektrik (Pumpenstecker, Tankgeber, Killkreis-Relais R1/R2/R3).

## Eckdaten

- Hersteller: Aprilia
- Modellfamilie: RSV (auf RSV Mille basierend)
- Baujahre: 2002–2005 (IE-E2)
- Einspritzung: Magneti Marelli IE-E2
- Kraftstoffsystem: ~3 bar Pumpendruck, 15 A Pumpensicherung

## Kraftstoffpumpenstecker (4-polig)

| Pin | Funktion | Kabelfarbe |
|---|---|---|
| 1 | +12 V Pumpe (von R2) | Rot (R) |
| 2 | Pumpe GND | Blau (B) |
| 3 | Tankgeber-Signal | Orange/Schwarz (Ar/N) |
| 4 | Tankgeber-GND | Blau/Schwarz (B/N) |

Tankgeber (Thermistor): voll < 14 Ω, leer 240–400 Ω.

## Sicherheits- und Kraftstoffrelais

- **R1 — Engine Stop Relay**: zentrales Kill-Element. Aktiv nur bei Zündung+Killschalter ein UND (Leerlauf ODER Seitenständer eingeklappt).
- **R2 — Fuel Pump Relay**: Prime-Funktion 2–3 s nach Zündung-Ein. Ausgang rot zum Pumpenstecker Pin 1.
- **R3 — Starter Relay**: Hochstrom-Schütz, sitzt separat nahe Batterie.

R1 und R2 sind oft baugleich unter der Sitzbank. Identifikation: R2 hat das rote Ausgangskabel zum Pumpenstecker.

## Diagnose-Reihenfolge bei „springt nicht an"

1. Sicherungen (Hauptsicherung 30 A, D 15 A, E 15 A)
2. R1 — Klick beim Zündung-Ein hörbar?
3. R2 — Pumpensummen (Prime) hörbar?
4. ECU-Steuerleitung zu R2
5. Pumpenwiderstand und Tankgeber gegen Nennwerte messen
6. Kill-/Seitenständer-/Neigungssensor prüfen, wenn R1 nicht zieht

## Confidence

Mittel. Werte aus aufbereiteter Werkstatt-Referenz, nicht aus Original-Aprilia-Schaltplan. Vor sicherheitskritischen Eingriffen mit Werkstatthandbuch abgleichen.

## Quellen

- [[aprilia-rsv-tuono-1000-elektrik]]
