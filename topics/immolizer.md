---
title: "Immolizer"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-10
tags: [immolizer, proptech, product]
confidence: medium
---

# Immolizer

## Summary

Immolizer ist als klare, nutzerseitige Marke für einen standardisierten Immobilien-Check gedacht. Das System soll Bewertung, Betriebskosten, Finanzierung und Vergleichbarkeit in einem kompakten, datenbasierten Report zusammenführen.

## Produktkern

- einseitiger Immobilien-Check oder Typenschein
- Community- und Marktvergleich über Benchmarks und Verteilungen
- nüchterne, standardisierte Darstellung statt Marketing-Sprache
- schneller Erstnutzen mit schlankem MVP

## Spannungen im Material

- `Immolizer` ist die Marke, `FlatRace` teils Projektname, teils Engine
- zusätzliche Naming-Varianten wie `LandingPay` oder `Flatpress` tauchen auf, wirken aber weniger stabil
- manche Dokumente wirken auf MVP fokussiert, andere gehen bereits stark in Plattformtiefe
- Scope reicht von einfacher Bewertung bis zu Portfolio-, Export- und Bewertungsplattform-Logik

## Wahrscheinlicher MVP-Kern

- Objekt-Erfassung
- Typenschein / A4-Report
- Community-Vergleich
- Betriebskosten-Analyse
- Basis-Export
- Auth und Projektstruktur

## PRD-Kern (aktuell)

Aus [[immolizer-prd]]:

1. **Onboarding** = 5–10 harte Fakten zur Immobilie
2. **Dashboard** = Vergleich mit Durchschnitt / Min / Max ähnlicher Objekte
3. **Widgets** pro Fakt als zentrales UI-Pattern
4. **Free + Paid** — Einstieg frei, Tiefe kostenpflichtig

## Datenmodell & Feldkatalog

Das fachliche Feldinventar liefert [[immobilien-kategorien]] — strukturiert nach **Wohnung / Haus / Grundstück** plus Querschnittsfelder (Medien, Scoring, Favoriten). Aus diesem Katalog werden die Onboarding-Fakten und die Widget-Achsen abgeleitet.

## Datenintegration (ImmoScout24)

Technische Ausgangslage siehe [[immoscout-datenintegration-source]]:

- **Legitimität**: Import/Export-API nur für eigene Inserate, Search-API nur mit Content-Partner-Freigabe — Marktdaten kein Selbstbedienungsladen
- **Architektur**: Adapter-Layer + Raw-Staging + versionierter Transformer + Canonical Listing Schema; Domain rechnet nur auf dem Canonical-Modell
- **Stolperfallen**: OAuth 1.0a server-side, Rate-Limit-Handling, getrennte Endpoints für Contact/Attachments/Publishing, Date-Felder ohne GMT

## Marktumfeld

Portal-Landschaft siehe [[eu-real-estate-platform-landscape]], vertieft durch [[eu-immobilienplattformen-deep]]. DACH-Fokus für den Start: ImmoScout24 (DE/AT), Willhaben (AT), Immowelt (DE), Kleinanzeigen (DE).

## UX-Referenzen

Open-Source Personal-Finance-Apps als Dashboard- und Widget-Vorbild: siehe [[open-source-finance-apps]]. Lizenzfilter (MIT/BSD/Apache ja, AGPL nur als Referenz) ist bei Code-Übernahme zu beachten.

## Relevante Quellen

- [[immolizer-source-migration]]
- [[flatrace-brainstorming]]
- [[immolizer-prd]]
- [[immobilien-kategorien]]
- [[immoscout-datenintegration-source]]
- [[eu-immobilienplattformen-deep]]
- [[open-source-finance-apps]]

## Verwandte Themen

- [[immoskill]] — fotozentrierte Immobilien- und Inventarakte; potenziell konvergent oder komplementär

## Relevante Projektseite

- [[Immolizer]]
