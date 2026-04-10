---
title: "Anwaltsliebling"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [legaltech, ai, austria, product]
confidence: medium
---

# Anwaltsliebling

## Summary

Anwaltsliebling ist als LegalTech-Produkt für juristische Laien gedacht: schneller Zugang zu strukturierter Ersteinschätzung, Fallaufbereitung und Dokumentenverständnis, bevor teure menschliche Beratung ins Spiel kommt.

## Wahrscheinlicher MVP

- Österreich als Startmarkt
- Rechtsbereiche: Erbrecht, Strafrecht, Baurecht
- Landingpage, Login, Payment, Onboarding, Dashboard, Feedbackformular
- Chat-/Projektlogik mit Fallhistorie und Dokument-Upload
- rollen- bzw. domänenspezifische KI-Workflows im Hintergrund

## Produktversprechen

- schneller als klassische Anwaltssuche und Terminlogik
- günstiger und strukturierter als klassische Erstberatung
- besser verständliche Aufbereitung für Nichtjuristen
- vorbereitetes Material für einen späteren Übergang an reale Anwälte

## Architektur-Richtung

- React-Frontend
- Supabase für Auth, Speicherung und schnelle Produktiteration
- Stripe für Zahlungen
- modulare Prompt-/Workflow-Struktur nach Land, Rechtsgebiet und Core-Bausteinen
- dynamische Mehrsprachigkeit statt komplett duplizierter Fachstruktur pro Sprache

## Kritische Spannungen

- KI-Auskunft versus echte Rechtsberatung ist rechtlich heikel
- Internationalisierung ist logisch, aber für den MVP gefährlich zu breit
- Qualität hängt stark an sauberen Rollen, Workflows, Quellen und Orchestrierung
- Vertrauen wird nur mit sehr klarer UX und hoher Antwortqualität entstehen

## Verwandte Richtungen

- [[anwaltsliebling-legaltech-brainstorm]]
- RATG/AHK-Kostenrechner als mögliches Satellitenprodukt oder Lead-Magnet
