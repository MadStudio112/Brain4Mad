---
title: "Aprilia RSV Tuono 1000 — Kraftstoff- und Relais-Referenz"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [aprilia, rsv-tuono, motorrad, elektrik, technik, source]
confidence: medium
---

# Aprilia RSV Tuono 1000 — Kraftstoffpumpe & Relais

## Summary

Technische Referenz für die Aprilia RSV Tuono 1000 (Modelljahre 2002–2005, IE-E2-Variante mit Magneti-Marelli-Einspritzung). Beschreibt Pinbelegung des Kraftstoffpumpensteckers (inkl. Kabelfarben, Tankgeber-Werte), die drei sicherheitsrelevanten Relais (R1 Motor-Stopp / R2 Kraftstoffpumpe / R3 Anlasser), deren Ansteuerung und Verkettung im Sicherheits-/Killkreis sowie typische Diagnose- und Fehlerbilder. Aufbereitete Werkstattdokumentation, vermutlich aus Aprilia-Werkstatthandbuch, Schaltplan und Forendiskussionen verdichtet.

## Key points

- Kraftstoffpumpenstecker 4-polig: Pin 1 +12 V (rot, vom R2-Ausgang), Pin 2 GND (blau), Pin 3 Tankgebersignal (orange/schwarz), Pin 4 Geber-GND (blau/schwarz)
- Tankgeber: Thermistor; voll < 14 Ω, leer 240–400 Ω; Kraftstoffpumpe über 15 A Sicherung
- R1 Engine Stop Relay = zentrales Kill-Element; nur aktiv bei Zündung+Killschalter ein UND (Leerlauf ODER Seitenständer eingeklappt); Umfallsensor schaltet ECU-seitig ab
- R2 Fuel Pump Relay: Spulen-Plus aus Sicherung D (geschaltet via R1), Spulen-Masse von ECU getaktet; Prime-Funktion 2–3 s nach Zündung
- R3 Starter Relay: Hochstrom-Schütz, Spulen-Plus aus Sicherung D, Masse über Startknopf + Kupplungs-/Leerlaufschalter; sitzt separat nahe Batterie
- R1 und R2 sind oft baugleich, im Halter unter der Sitzbank — Identifikation am rotem Ausgangskabel von R2
- Diagnose-Reihenfolge: Sicherungen → R1 (Klick beim Zündung-Ein) → R2 (Pumpensummen) → ECU-Steuerleitung → Pumpenwiderstand → Tankgeber
- Typische Fehlerbilder: heiße Relais bei blockierter Pumpe, kein Prime nach Zündung-Ein deutet auf R2/ECU/Sicherung D, kein Killrelais-Klick → R1, Killschalter, Seitenständer- oder Neigungssensor

## Important themes

- Sicherheitskette: Zündschloss → Killschalter → R1 → Sicherungen D/E → R2/R3 → Pumpe/Anlasser
- Diodenmodul kombiniert Seitenständer- und Leerlauf-Signal für die Start-/Stopplogik
- Kabelfarbencode des Aprilia-Schaltplans (Ar = orange, R = rot, B = blau, N = schwarz, B/N, Ar/N etc.)
- Position der Komponenten unter der Sitzbank rechts/hinten neben Batterie und ECU

## Open questions

- Exakte Pinnummer am ECU-Stecker für die R2-Steueranleitung im IE-E2-Modell (im Text Pin 16 am 16-poligen Stecker — gegen Werkstatthandbuch verifizieren)
- Unterschiede zwischen RSV Mille und Tuono in der Verkabelung — Text behandelt sie weitgehend identisch
- Originale Aprilia-Teilenummern und Beschaffungspfade (Doku enthält keine Bestellangaben)

## Risks / caveats

- Quelle ist eine aufbereitete Zusammenfassung, kein Original-Werkstatthandbuch — Pinbelegungen und Sicherungsbezeichnungen vor sicherheitskritischen Eingriffen mit dem Schaltplan abgleichen
- Kabelfarben können je nach Marktversion und Modelljahr leicht abweichen

## File reference

- `raw/notes/aprilia-rsv-tuono-1000.md`
