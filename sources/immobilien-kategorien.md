---
title: "Immobilien-Kategorien (Feldkatalog)"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [immolizer, datenmodell, real-estate]
confidence: high
---

# Immobilien-Kategorien (Feldkatalog)

Quelle: `raw/notes/immobilien-kategorien.md`

## Inhalt

Praxisnaher Feldkatalog für ein Immobilienportal, strukturiert nach drei Objekttypen:

### 1. Wohnung
Grunddaten · Preise & Kosten · Energie & Technik · Ausstattung · Gebäude & Gemeinschaft · Parken · Rechtliches · Lage

### 2. Haus
Grunddaten · Preise & Kosten · Energie & Technik · Ausstattung · Bau & Substanz · Parken · Außenanlagen · Rechtliches · Lage

### 3. Grundstück
Grunddaten · Preise & Kosten · Widmung & Nutzung · Erschließung · Rechtliches · Lage & Umfeld

### Querschnitt (alle Typen)
Suchstatus, Objektnummer, Anbieter, Inseratsdatum, Fotos, Grundrisse, Videos, Exposé, Vergleichskennzahlen, Bewertungs-Score, Favoriten.

## Einordnung

Der Katalog definiert das fachliche Feldinventar, aus dem [[immolizer]] seine 5–10 Onboarding-Fakten selektieren kann. Er ist stärker nutzerzentriert als das rohe ImmoScout-Feldschema aus [[immoscout-datenintegration-source]] und liefert die natürliche Gruppenstruktur für das Widget-Layout des Dashboards.

## Verwendung

- Ableitung der Canonical-Listing-Felder für Immolizer
- Mapping-Zielstruktur beim ImmoScout-Adapter
- Filter- und Vergleichsachsen im Dashboard
