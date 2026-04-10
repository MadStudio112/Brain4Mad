# Projektanforderungsdokument (PRD)

## 1. Projekt-Übersicht
- **Projektname:** FlatRace
- **Kurzbeschreibung:** Plattform zur standardisierten Erfassung, Analyse und Vergleichbarkeit von Immobilien. Zentrales Artefakt ist der „Typenschein“ – eine einseitige, visuelle Zusammenfassung mit Community-Vergleich (Normalverteilung).
- **Zielsetzung:** Objektive, transparente und datenbasierte Einordnung von Immobilien – unabhängig von Vermarktungsinteressen.
- **Vision:** FlatRace als Standard für transparente Immobilienbewertung – lokal bis international.

---

## 2. Ziele & Erfolgskriterien (KPIs)
- **Time-to-Typenschein:** < 2 Minuten bis zur ersten vollständigen Erfassung
- **Datenqualität:** ≥ 95% Pflichtfelder vollständig je Typenschein
- **Community-Abdeckung:** ≥ 1.000 Datensätze pro Region (DACH Start)
- **Vergleichs-Engagement:** ≥ 60% Nutzer sehen Community-Vergleich
- **Exportnutzung:** ≥ 40% generieren Exposé/PDF
- **Performance:** FCP < 2s, TTI < 3s (breitband), p95 API < 300ms

---

## 3. Scope
- **In-Scope:**
  - Typenschein (einseitiges Datenblatt)
  - Community-Vergleich (Normalverteilung)
  - Betriebskosten-Analyse
  - Exposé-Generator (mehrseitig)
  - SAS 360 (Vergleich mehrerer eigener Objekte)
  - i18n DE/EN
  - Auth (E-Mail/Passwort, Google; Supabase)
- **Out-of-Scope (v1):**
  - End-to-End-Verschlüsselung (Seven23-Ansatz)
  - Marktplatz-/Vermarktungsfunktionen
  - Mobile App (native)
  - Komplexe Gutachten-Workflows mit Signatur

---
- **In-Scope:**
  - Typenschein (einseitiges Datenblatt)
  - Community-Vergleich (Normalverteilung)
  - Betriebskosten-Analyse
  - Exposé-Generator (mehrseitig)
  - SAS 360 (Vergleich mehrerer eigener Objekte)
  - i18n DE/EN
  - Auth (E-Mail/Passwort, Google; Supabase)
- **Out-of-Scope (v1):**
  - End-to-End-Verschlüsselung (Seven23-Ansatz)
  - Marktplatz-/Vermarktungsfunktionen
  - Mobile App (native)
  - Komplexe Gutachten-Workflows mit Signatur

---

## 4. Kernfunktionen (mit Akzeptanzkriterien)
### 4.1 Typenschein (Datenblatt)
- Inhalt: Wohnfläche, Zimmer, Baujahr, Energie, Ausstattung, Lage, Kosten, Kennzahlen.
- Darstellung: einseitig, klar strukturiert, druck- und weboptimiert.
- **AK:** Pflichtfelder validiert; PDF/HTML-Export erzeugt reproduzierbares Layout.
- Einseitige, standardisierte Übersicht aller Immobiliendaten
- Visualisiert wie ein „Blutbild“ oder TÜV-Bericht
- Darstellung von Flächen, Zimmern, Baujahr, Ausstattung, Energieform usw.

### 4.2 Community-Vergleich (Normalverteilung)
- Vergleich von Objektwerten mit regionalen Mittelwerten/Quantilen.
- Darstellung: Histogramm, Position (z-Score), Ausreißer.
- **AK:** Für ≥80% Felder mit Community-Daten werden Vergleichswerte angezeigt; p95 Latenz < 300ms.
- Vergleich eigener Werte mit regionalen oder nationalen Durchschnittsdaten
- Visualisierung von Ausreißern, Mittelwerten und Verteilungen
- Bewertung der Position im Markt (unter/über dem Durchschnitt)

### 4.3 Betriebskosten-Analyse
- Eingabe: monatliche Kostenkategorien (Heizung, Strom, Wasser, Hausverwaltung …).
- Vergleich: Community-Schnitt, Abweichung in €/%.
- **AK:** Vollständige Berechnung, Zeitreihen (optional), Export möglich.
- Eingabe monatlicher/nutzerbezogener Betriebskosten
- Vergleich mit Community-Schnitt
- Abweichungsberechnung in € und %

### 4.4 Exposé-Generator
- Mehrseitiger Export (PDF/HTML) mit Textbausteinen.
- Stil: neutral bis leicht emotional, Branding anpassbar.
- **AK:** Export ohne manuelle Nachbearbeitung verwendbar; Platzhalter werden ersetzt.
- Erzeugt ein professionelles, mehrseitiges Exposé aus denselben Daten
- Automatische Textgenerierung (neutral bis emotional)
- Für Verkauf oder Vermietung nutzbar

### 4.5 SAS 360 – Vergleichs-Dashboard
- Vergleich mehrerer eigener Objekte; Kennzahlen, Rangfolge, Filter.
- **AK:** Mind. 3 Objekte vergleichbar; Sortierung/Filterung reaktiv.
- Vergleich mehrerer eigener Immobilien
- Portfolio-Analyse (z. B. für Investoren, Verwaltungen)
- Kennzahlenübersicht & Exportfunktionen

### 4.6 Bewertungsplattform (v2+)
- Dienstleister-Bewertungen, Transparenz-Kennzahlen.
- **AK:** CRUD, Moderation, Aggregation.
- Nutzer können Gutachter, Anwälte, Handwerker etc. bewerten
- Transparente Erfahrungswerte zur Qualität & Zuverlässigkeit
- Optionale Verbindung zu Immobilienprojekten

---

## 5. User Flows
- **Onboarding & Auth:** Sign-up/Sign-in (Supabase Auth), erstes Objekt anlegen.
- **Objekt-Erfassung:** Schrittweiser Wizard mit Validierung, Autosave.
- **Analyse:** Dashboard → Typenschein → Community-Ansicht → Export.
- **Portfolio:** Objekte vergleichen (SAS 360), Favoriten/Notizen.
- **Exposé:** Auswahl Layout → Vorschau → Export.

---

## 6. Informationsarchitektur
- Views: `Dashboard`, `Property`, `Expose`, `SAS360`, `Auth`.
- Komponenten: Form-Sektionen, Charts (Community), KPIs, Export.
- Navigation: Oben (Tabs) + Kontextaktionen (rechts).

---

## 7. Datenmodell (vereinfachter Entwurf)
- `properties`
  - id, user_id, title, location_geo, area_m2, rooms, year_built, energy_type, amenities(jsonb), operating_costs(jsonb), created_at, updated_at
- `community_stats`
  - region_key, metric_key, distribution_params(jsonb), sample_size, updated_at
- `users` (Supabase Auth)
- `exports`
  - property_id, type(pdf|html), metadata(jsonb), created_at
- `ratings` (v2+)
  - subject_type, subject_id, score, comment, user_id, created_at

---

## 8. Tech Stack & Architektur
- **Frontend:** React + TypeScript, Redux Toolkit (global state/caching), React Router, Chart.js, Material UI, i18next.
- **Datenzugriff:** Supabase JS Client; selektive Serverfunktionen (Edge Functions optional).
- **Backend/DB:** Supabase (Postgres, RLS, Auth).
- **State-Management:** Redux Toolkit + RTK Query (oder React Query) für API-Caching.
- **Build/Dev:** Vite (oder Webpack), ESLint/Prettier, Jest/RTL, Playwright (E2E).
- **Konfiguration:** `.env` (REACT_APP_* / VITE_*).

---

## 9. API & Policies (Supabase)
- CRUD auf `properties`, RLS: Nutzer sehen eigene Objekte; Community-Endpunkte liefern anonymisierte, aggregierte Werte.
- Aggregation: SQL-Views/Materialized Views für Community-Verteilungen (Normalverteilung: µ, σ, n).
- Rate Limiting: Edge/Row-Level via Supabase Policies/Functions.
- Webhooks (optional): Export-Fertigstellung.

---

## 10. Sicherheit & Datenschutz
- Auth: Supabase (E-Mail/Passwort, Google; Apple später).
- RLS: Striktes Owner-Modell für private Daten.
- Community-Daten: Aggregiert/anonymisiert; keine Rekonstruktion individueller Datensätze.
- Secrets: nur serverseitig; kein Hardcoding.
- Audit: Änderungsprotokoll auf `properties` (trigger-based).

---

## 11. Nicht-funktionale Anforderungen
- Leistung: FCP < 2s, TTI < 3s; p95 API < 300ms; Bundle < 300KB (gzipped) v1.
- Zuverlässigkeit: 99.5% Verfügbarkeit; Backups täglich.
- Barrierefreiheit: WCAG 2.1 AA.
- Internationalisierung: DE/EN, spätere Erweiterung via Namespace-Dateien.
- Observability: Basis-Logging, Sentry (Fehler), einfache Metriken (page/API).

---

## 12. Analytics & Tracking
- Events: Onboarding abgeschlossen, Property erstellt/aktualisiert, Vergleich geöffnet, Export durchgeführt.
- Datenschutzkonform (Banner/Opt-in); anpassbar via `src/lib/analytics.ts`.

---

## 13. Akzeptanzkriterien (gesamt)
- Typenschein generierbar ohne Fehler
- Community-Vergleich verfügbar für Kernmetriken (Fläche, Zimmer, Kosten)
- Export (PDF/HTML) stabil und CI-baut
- Auth + RLS korrekt
- i18n vollständig für DE/EN

---

## 14. Roadmap (v1 → v2)
- **v1 (MVP):** Typenschein, Community-Vergleich (µ/σ), Betriebskosten, Export (Basis), Auth, i18n, Redux+Supabase Integration.
- **v1.1:** SAS 360, verbesserte Charts, Materialized Views.
- **v2:** Dienstleister-Bewertungen, erweiterte Exposé-Layouts, mobile Optimierung Plus.

---

## 15. Risiken & Annahmen
- Datenbasis-Qualität (Sample Size je Region)
- DSGVO & Anonymisierung bei Community-Daten
- Performance bei großen Aggregationen → Materialized Views nötig
- UI-Konsistenz (Charts/Export) über Browser hinweg

---

## 16. Offene Fragen
- Regionen-Taxonomie (PLZ, Stadtteil, Raster?)
- Pflichtfelder für Typenschein v1 (Minimalset)
- Export-Engine (Server- vs Client-PDF, z. B. Puppeteer vs jsPDF)
- RTK Query vs React Query final?
- Branding/Theme-Vorgaben


---

