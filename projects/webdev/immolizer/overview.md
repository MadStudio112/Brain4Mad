---
title: "Immolizer"
type: project
status: active
created: 2026-04-09
updated: 2026-04-11
tags: [immolizer, proptech, product]
confidence: medium
aliases: [immolizer, Immolizer]
family: _immolizer-family
---

# Immolizer

## Summary

Immolizer soll Immobilienbewertung, Kosten, Finanzierung und Marktvergleich in einem klaren, standardisierten System bündeln. Kernartefakt ist ein kompakter Report, der Objekte nüchtern gegen Markt- und Community-Daten spiegelt.

## Repo

`C:\Users\Mad\Code\MadStudio112\Immolizer-v0` — aktuelles Entwicklungs-Repo (Brownfield-Monorepo). Naming und Familienzuordnung: [[_immolizer-family]].

## Produktkern

- einseitiger Immobilien-Check / Typenschein
- Community- und Marktvergleich über Benchmarks und Verteilungen
- nüchterne, standardisierte Darstellung statt Marketing-Sprache
- schneller Erstnutzen mit schlankem MVP

## Spannungen im Material

- `Immolizer` ist die Marke, `FlatRace` teils Projektname, teils Engine
- Scope reicht von einfacher Bewertung bis zu Portfolio-, Export- und Bewertungsplattform-Logik

## Wahrscheinlicher MVP-Kern

- Objekt-Erfassung
- Typenschein / A4-Report
- Community-Vergleich
- Betriebskosten-Analyse
- Basis-Export
- Auth und Projektstruktur

## PRD-Kern

Aus [[brief]]:

1. **Onboarding** = 5–10 harte Fakten zur Immobilie
2. **Dashboard** = Vergleich mit Durchschnitt / Min / Max ähnlicher Objekte
3. **Widgets** pro Fakt als zentrales UI-Pattern
4. **Free + Paid** — Einstieg frei, Tiefe kostenpflichtig

## Datenmodell & Feldkatalog

Das fachliche Feldinventar liefert [[immobilien-kategorien]] — strukturiert nach **Wohnung / Haus / Grundstück** plus Querschnittsfelder (Medien, Scoring, Favoriten).

## Datenintegration (ImmoScout24)

Technische Ausgangslage: [[immoscout-datenintegration-source]]:

- **Legitimität**: Import/Export-API nur für eigene Inserate, Search-API nur mit Content-Partner-Freigabe
- **Architektur**: Adapter-Layer + Raw-Staging + versionierter Transformer + Canonical Listing Schema
- **Stolperfallen**: OAuth 1.0a server-side, Rate-Limit-Handling, getrennte Endpoints, Date-Felder ohne GMT

## Marktumfeld

Portal-Landschaft: [[eu-real-estate-platform-landscape]], vertieft durch [[eu-immobilienplattformen-deep]].

## UX-Referenzen

Open-Source Personal-Finance-Apps als Dashboard- und Widget-Vorbild: [[open-source-finance-apps]].

## Materialstand

Das migrierte Nextra-Wiki-Material ist ungewöhnlich weit: Strategie, PRD, Architektur, UX, UI, Ops, Sprint, Marketing und Legal sind angelegt. Das ist kein loses Brainstorming, sondern ein vorstrukturiertes Projekthirn. Weitere Arbeit sollte aus Konsolidierung, Priorisierung und Widerspruchsbereinigung bestehen — nicht aus neuen Ideen.

## Nächste Schritte

- Kernthese und Naming Immolizer vs. FlatRace konsolidieren (→ [[_immolizer-family]])
- MVP-Scope auf eine belastbare Kurzfassung verdichten
- Widersprüche im Scope-Material bereinigen

## Quellen

- [[_source-migration]]
- [[flatrace-brainstorming]]
- [[brief]]
- [[immobilien-kategorien]]
- [[immoscout-datenintegration-source]]
- [[eu-immobilienplattformen-deep]]

## Offene Fragen

→ [[questions]]

## Verwandte Themen

- [[immoskill]] — fotozentrierte Immobilien- und Inventarakte
