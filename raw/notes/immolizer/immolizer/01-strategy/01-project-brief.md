# Project Brief – FlatRace

## Zielgruppe / ICP
- Private Eigentümer:innen, Makler:innen, kleine Verwaltungen (DACH, Start DE)
- Need: schnelle, neutrale Einschätzung und Vergleichbarkeit von Immobilien

## Problem
- Immobiliendaten sind fragmentiert, intransparent und schwer vergleichbar.
- Exposés sind häufig marketinggetrieben, nicht standardisiert.

## Lösung / Produktkern
- „Typenschein“: einseitiges, standardisiertes Datenblatt pro Objekt
- Community-Vergleich: Normalverteilung je Kennzahl (µ, σ, n) mit Position des Objekts
- Export: PDF/HTML für Exposé und Reporting

## UVP / Differenzierung
- Neutral, datenbasiert, standardisiert (kein Vermarktungsfokus)
- Schnelligkeit: Time-to-Typenschein < 2 Minuten
- Vergleich auf Community-Basis statt Einzelmeinung

## Top-KPIs
- Time-to-Typenschein < 2 Min
- ≥ 95% Pflichtfelder vollständig
- ≥ 60% Nutzer öffnen Community-Vergleich

## Scope v1 (In/Out)
- In: Typenschein, Community-Vergleich, Betriebskosten, Export, Auth (Supabase), i18n (DE/EN)
- Out: Marktplatz, native App, komplexe Gutachten-Workflows, E2E-Verschlüsselung (v2+)

## Risiken & Annahmen (Top 3)
- Datenbasis je Region ausreichend groß (n) – Annahme: Sampling via Community wächst
- DSGVO-konforme Aggregation/Anonymisierung – Risiko bei kleinen n
- Export-Engine stabil im CI/Browser

## Meilensteine (nächste 4–6 Wochen)
1. PRD stabilisieren, overview/Plan konsolidieren
2. Datenmodell/Policies (Supabase) definieren
3. Form-Wizard (Typenschein) MVP + Autosave
4. Community-Chart (µ/σ) + Basis-Export

Owner: Product/Tech (gemeinsam), Daten: wöchentliches Update
