---
title: "Aprilia RSV Tuono 1000 (2002–2005)"
type: entity
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [aprilia, rsv-tuono, motorrad, naked-bike, technik]
confidence: medium
---

# Aprilia RSV Tuono 1000 (2002–2005)

## Summary

Italienisches Naked-Bike auf Basis der RSV Mille Sportlerplattform, gebaut 2002–2005 mit IE-E2-Magneti-Marelli-Einspritzung. Hier dokumentiert primär als technische Referenz für Kraftstoff- und Sicherheitselektrik (Pumpenstecker, Tankgeber, Killkreis-Relais R1/R2/R3). Vollständige technische Tiefe siehe [[aprilia-rsv-tuono-1000-elektrik]] Quellnotiz.

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

- **R1 — Engine Stop Relay**: zentrales Kill-Element. Aktiv nur bei Zündung+Killschalter ein UND (Leerlauf ODER Seitenständer eingeklappt). Speist Sicherungen D und E für die nachgelagerten Motorkreise. Umfallsensor schaltet ECU-seitig ab.
- **R2 — Fuel Pump Relay**: Spulen-Plus aus Sicherung D (geschaltet via R1), Spulen-Masse von der ECU getaktet. Prime-Funktion 2–3 s nach Zündung-Ein. Ausgang rot zum Pumpenstecker Pin 1.
- **R3 — Starter Relay**: Hochstrom-Schütz, sitzt separat nahe Batterie. Spulen-Plus aus Sicherung D, Spulen-Masse über Startknopf + Kupplungs-/Leerlaufschalter.

R1 und R2 sind oft baugleich und unter der Sitzbank im Halter neben Batterie und ECU. Identifikation: R2 hat das rote Ausgangskabel zum Pumpenstecker.

## Diagnose-Reihenfolge bei „springt nicht an"

1. Sicherungen (Hauptsicherung 30 A, D 15 A, E 15 A)
2. R1 — Klick beim Zündung-Ein hörbar?
3. R2 — Pumpensummen (Prime) hörbar?
4. ECU-Steuerleitung zu R2 (Pin am 16-poligen ECU-Stecker — vor Eingriff mit Werkstatthandbuch verifizieren)
5. Pumpenwiderstand und Tankgeber gegen Nennwerte messen
6. Kill-/Seitenständer-/Neigungssensor prüfen, wenn R1 nicht zieht

## Beziehungen

- Verwandte Modelle: RSV Mille (Sportler-Schwestermodell, weitgehend identische Elektrik)

## Confidence

Mittel. Werte stammen aus einer aufbereiteten Werkstatt-Referenz, nicht aus dem Original-Aprilia-Schaltplan. Vor sicherheitskritischen Eingriffen mit dem Werkstatthandbuch des konkreten Modelljahrs abgleichen. Kabelfarben können je nach Marktversion variieren.

## Relevante Quellen

- [[aprilia-rsv-tuono-1000-elektrik]] (Quellnotiz)
