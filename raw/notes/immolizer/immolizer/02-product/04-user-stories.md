# User Stories – FlatRace

## Übersicht
Dieses Dokument enthält alle User Stories für FlatRace, strukturiert nach Epics und priorisiert nach MoSCoW. Jede Story folgt dem Format: "Als [Rolle] möchte ich [Funktion], damit [Nutzen]".

## Epic 1: Core Property Management

### US-001: Typenschein erstellen (Must Have)
**Als** privater Immobilienbesitzer
**möchte ich** ein standardisiertes Datenblatt für meine Wohnung erstellen
**damit ich** eine objektive Bewertung und Vergleichbarkeit habe

**Akzeptanzkriterien:**
- [ ] Pflichtfelder werden validiert (Adresse, Wohnfläche, Zimmer, Baujahr)
- [ ] Autosave funktioniert alle 30 Sekunden
- [ ] Fortschrittsanzeige zeigt Vollständigkeit
- [ ] Einseitiges Layout ist druckoptimiert
- [ ] Time-to-Complete < 2 Minuten

**Story Points:** 8
**Priorität:** Must Have
**Epic:** F-001

---

### US-002: Community-Vergleich anzeigen (Must Have)
**Als** Immobilieninteressent
**möchte ich** meine Wohnung mit regionalen Vergleichswerten sehen
**damit ich** weiß, ob sie über oder unter dem Marktdurchschnitt liegt

**Akzeptanzkriterien:**
- [ ] Normalverteilung wird als Histogramm dargestellt
- [ ] Meine Position wird als Z-Score und Percentile angezeigt
- [ ] Vergleichswerte für ≥80% der Metriken verfügbar
- [ ] Ladezeit < 300ms für Community-Lookups
- [ ] Klare Kommunikation: "über/unter Durchschnitt"

**Story Points:** 5
**Priorität:** Must Have
**Epic:** F-002

---

### US-003: Dashboard-Übersicht (Should Have)
**Als** Mehrfach-Eigentümer
**möchte ich** alle meine Immobilien auf einen Blick sehen
**damit ich** den Überblick über mein Portfolio behalte

**Akzeptanzkriterien:**
- [ ] Alle Objekte in übersichtlicher Liste dargestellt
- [ ] Status-Filter (Entwurf/Published/Archiviert) funktionieren
- [ ] Quick-Actions für Bearbeiten und Exportieren verfügbar
- [ ] Responsive Design für Mobile/Desktop
- [ ] Sortierung nach Datum, Titel, Status möglich

**Story Points:** 3
**Priorität:** Should Have
**Epic:** F-003

---

### US-004: PDF-Export generieren (Must Have)
**Als** Makler
**möchte ich** ein professionelles Exposé-PDF erstellen
**damit ich** es meinen Kunden präsentieren kann

**Akzeptanzkriterien:**
- [ ] Typenschein als einseitiges PDF generiert
- [ ] Exposé als mehrseitiges PDF mit Layout-Optionen
- [ ] Async-Processing mit Status-Updates
- [ ] Download-Link per E-Mail
- [ ] Export ohne manuelle Nachbearbeitung verwendbar

**Story Points:** 5
**Priorität:** Must Have
**Epic:** F-004

---

## Epic 2: Operating Costs & Analysis

### US-005: Betriebskosten eingeben (Must Have)
**Als** Vermieter
**möchte ich** die monatlichen Betriebskosten meiner Wohnung erfassen
**damit ich** die Wirtschaftlichkeit transparent darstellen kann

**Akzeptanzkriterien:**
- [ ] Alle Standard-Kostenkategorien verfügbar (Heizung, Strom, Wasser, etc.)
- [ ] Automatische Berechnung der Gesamtkosten
- [ ] Unterstützung verschiedener Perioden (monatlich/quartalsweise)
- [ ] Validierung verhindert negative Werte
- [ ] Kosten pro m² werden automatisch berechnet

**Story Points:** 3
**Priorität:** Must Have
**Epic:** F-005

---

### US-006: Kosten-Vergleich mit Community (Should Have)
**Als** Eigentümer
**möchte ich** meine Betriebskosten mit dem regionalen Durchschnitt vergleichen
**damit ich** weiß, ob meine Kosten angemessen sind

**Akzeptanzkriterien:**
- [ ] Abweichung in € und % angezeigt
- [ ] Community-Schnitt für alle Kostenkategorien verfügbar
- [ ] Mindestens n=10 Vergleichsobjekte erforderlich
- [ ] Kosten-Optimierungsvorschläge angezeigt
- [ ] Historische Entwicklung über Zeit

**Story Points:** 5
**Priorität:** Should Have
**Epic:** F-006

---

## Epic 3: Advanced Features

### US-007: Portfolio-Vergleich (Should Have)
**Als** Investor
**möchte ich** mehrere Immobilien miteinander vergleichen
**damit ich** die Performance meines Portfolios analysieren kann

**Akzeptanzkriterien:**
- [ ] Mindestens 3 Objekte können verglichen werden
- [ ] Sortierung und Filterung funktionieren reaktiv
- [ ] Kennzahlen als Tabelle und Charts dargestellt
- [ ] Export der Vergleichsdaten möglich
- [ ] Rangfolge nach verschiedenen Kriterien

**Story Points:** 8
**Priorität:** Should Have
**Epic:** F-007

---

### US-008: Verschiedene Export-Templates (Could Have)
**Als** Makler
**möchte ich** verschiedene Exposé-Layouts verwenden
**damit ich** das passende Design für unterschiedliche Kunden wählen kann

**Akzeptanzkriterien:**
- [ ] Mindestens 3 verschiedene Templates verfügbar
- [ ] Stil von neutral bis emotional anpassbar
- [ ] Branding individuell konfigurierbar
- [ ] Vorschau vor Export verfügbar
- [ ] Template-Editor für individuelle Anpassungen

**Story Points:** 8
**Priorität:** Could Have
**Epic:** F-008

---

## Epic 4: Platform Features

### US-009: Dienstleister bewerten (Could Have)
**Als** Immobilienbesitzer
**möchte ich** Handwerker und Dienstleister bewerten
**damit ich** anderen bei der Auswahl helfen kann

**Akzeptanzkriterien:**
- [ ] Vollständiges CRUD für Bewertungen
- [ ] Moderation verhindert Missbrauch
- [ ] Durchschnittsbewertungen werden aggregiert
- [ ] Verbindung zu Immobilienprojekten möglich
- [ ] Bewertungen sind öffentlich einsehbar

**Story Points:** 8
**Priorität:** Could Have
**Epic:** F-009

---

## Sprint-Ready Stories

### **Sprint 1: Foundation (Must Have)**
**Ziel:** Basis-Funktionalität für Typenschein-Erstellung

- US-001: Typenschein erstellen (8 SP)
- US-005: Betriebskosten eingeben (3 SP)
- US-003: Dashboard-Übersicht (3 SP)

**Sprint-Ziel:** Erster vollständiger User Flow von Erstellung bis Übersicht

---

### **Sprint 2: Analysis & Export (Must Have)**
**Ziel:** Analyse-Funktionen und Dokumenten-Export

- US-002: Community-Vergleich anzeigen (5 SP)
- US-004: PDF-Export generieren (5 SP)

**Sprint-Ziel:** Komplette Analyse und Export-Funktionalität

---

### **Sprint 3: Enhanced Analysis (Should Have)**
**Ziel:** Erweiterte Analyse-Funktionen

- US-006: Kosten-Vergleich mit Community (5 SP)
- US-007: Portfolio-Vergleich (8 SP)

**Sprint-Ziel:** Vollständige Analyse-Suite für Profi-Nutzer

---

### **Sprint 4: Platform Features (Could Have)**
**Ziel:** Erweiterte Plattform-Funktionalität

- US-008: Verschiedene Export-Templates (8 SP)
- US-009: Dienstleister bewerten (8 SP)

**Sprint-Ziel:** Plattform zu vollständiger Lösung erweitern

---

## Story Acceptance Template

### **Definition of Ready (DoR)**
Eine Story ist "Ready", wenn:
- [ ] Titel folgt Format: "Als [Rolle] möchte ich [Funktion], damit [Nutzen]"
- [ ] Akzeptanzkriterien sind SMART (Specific, Measurable, Achievable, Relevant, Time-bound)
- [ ] Story Points sind geschätzt (1-13 SP)
- [ ] Abhängigkeiten sind identifiziert
- [ ] Epic-Zuordnung ist klar
- [ ] Priorität nach MoSCoW ist gesetzt

### **Definition of Done (DoD)**
Eine Story ist "Done", wenn:
- [ ] Alle Akzeptanzkriterien erfüllt sind
- [ ] Code ist reviewed und approved
- [ ] Unit-Tests sind geschrieben und bestanden
- [ ] Integration-Tests sind bestanden
- [ ] Dokumentation ist aktualisiert
- [ ] Feature ist deployed und funktioniert in Production
- [ ] Performance-Kriterien sind erfüllt
- [ ] Accessibility-Standards sind eingehalten

---

## Story Dependencies Matrix

| Story | Abhängigkeiten | Blockiert | Blockiert von |
|-------|---------------|-----------|---------------|
| US-001 | Auth-System, Datenmodell | US-002, US-003, US-004 | - |
| US-002 | Community-Stats-API | - | US-001 |
| US-003 | Property-Liste-API | - | US-001 |
| US-004 | Export-Engine | - | US-001 |
| US-005 | Operating-Costs-Schema | US-006 | - |
| US-006 | Community-Stats-API | - | US-005 |
| US-007 | Property-System, Charts | - | US-001 |
| US-008 | PDF-Export | - | US-004 |
| US-009 | Rating-System | - | - |

---

## Story Points Guidelines

### **1-3 Story Points (Small)**
- Einfache UI-Änderungen
- CRUD-Operationen
- Form-Validierung
- API-Endpoints ohne komplexe Logik

### **5-8 Story Points (Medium)**
- Neue Features mit UI und Backend
- Integration mit externen Services
- Komplexe Validierungslogik
- Chart-Implementierungen

### **13+ Story Points (Large)**
- Komplexe Algorithmen (Community-Stats)
- Neue System-Architekturen
- Integration mehrerer Services
- Performance-kritische Features

---

## Burndown & Velocity Tracking

### **Sprint Capacity**
- **Team Size:** 2-3 Entwickler
- **Sprint Length:** 2 Wochen
- **Velocity Target:** 20-25 Story Points pro Sprint

### **Risk Stories**
**Stories mit hohem Risiko:**
- US-002: Community-Stats Performance (< 300ms)
- US-004: PDF-Export Async-Processing
- US-007: Portfolio-Vergleich mit Charts

**Mitigation:**
- Early Prototyping für Performance-kritische Stories
- Pair Programming für komplexe Algorithmen
- Buffer-Time für unerwartete Komplexität

---

## Backlog Grooming Guidelines

### **Wöchentliches Grooming:**
- Neue Stories werden priorisiert und geschätzt
- Akzeptanzkriterien werden verfeinert
- Dependencies werden aktualisiert
- Sprint Ready Stories werden identifiziert

### **Story Lifecycle:**
1. **New:** Idee oder Anforderung
2. **Refined:** Akzeptanzkriterien definiert
3. **Ready:** Sprint-tauglich
4. **In Progress:** Aktiv in Entwicklung
5. **Done:** Alle Kriterien erfüllt

---

## Success Metrics

### **Story-Level Metrics**
- **Lead Time:** Von Story-Erstellung bis Done
- **Cycle Time:** Von In Progress bis Done
- **Bug Rate:** Bugs pro Story Point
- **Rejection Rate:** Stories, die nicht im ersten Versuch accepted werden

### **Team Metrics**
- **Velocity Trend:** Story Points pro Sprint
- **Predictability:** Geschätzte vs. tatsächliche Velocity
- **Quality:** Bugs pro 100 Story Points
- **Satisfaction:** Team-Zufriedenheit mit Story-Qualität
