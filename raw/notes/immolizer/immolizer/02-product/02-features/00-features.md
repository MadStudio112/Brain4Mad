# Features Overview – FlatRace

## Übersicht
Dieser Index listet alle Features von FlatRace mit Priorisierung (MoSCoW), Status und Verlinkung zu detaillierten Spezifikationen. Die Features sind nach Epics gruppiert und folgen der Roadmap v1 → v2.

## Feature-Priorisierung (MoSCoW)

### **Must Have (v1 MVP)**
Kritische Features für den Markteintritt - ohne diese funktioniert das Produkt nicht.

### **Should Have (v1.1)**
Wichtige Features für bessere Nutzererfahrung - werden nach dem MVP implementiert.

### **Could Have (v2)**
Nützliche Features für erweiterte Funktionalität - werden bei verfügbaren Ressourcen implementiert.

### **Won't Have (v2+)**
Features die bewusst nicht implementiert werden oder für spätere Versionen geplant sind.

---

## Epic 1: Core Property Management

### F-001: FlatForm (Typenschein-Erfassung)
- **Status:** Draft
- **Priorität:** Must Have
- **Spec:** [01-flat-form.md](01-flat-form.md)
- **Beschreibung:** Einseitiges, standardisiertes Datenblatt für Immobilien
- **Akzeptanzkriterien:**
  - [ ] Pflichtfelder werden validiert (Wohnfläche, Zimmer, Baujahr, Energie)
  - [ ] Autosave funktioniert alle 30 Sekunden
  - [ ] Time-to-Typenschein < 2 Minuten
  - [ ] Einseitiges Layout ist druck- und weboptimiert
- **Aufwand:** 8 Story Points
- **Abhängigkeiten:** Datenmodell, Auth-System

### F-002: Normal Distribution (Community-Vergleich)
- **Status:** Draft
- **Priorität:** Must Have
- **Spec:** [02-normal-distribution.md](02-normal-distribution.md)
- **Beschreibung:** Vergleich eigener Werte mit regionalen Community-Daten
- **Akzeptanzkriterien:**
  - [ ] Für ≥80% Felder werden Community-Vergleichswerte angezeigt
  - [ ] Normalverteilung wird als Histogramm dargestellt
  - [ ] Position des Objekts wird als Z-Score und Percentile angezeigt
  - [ ] p95 Latenz < 300ms für Community-Lookups
- **Aufwand:** 13 Story Points
- **Abhängigkeiten:** Community-Stats, Chart-Engine

### F-003: Dashboard (Übersicht)
- **Status:** Draft
- **Priorität:** Should Have
- **Spec:** [03-dashboard.md](03-dashboard.md)
- **Beschreibung:** Zentrale Übersicht aller Objekte mit KPIs und Quick-Actions
- **Akzeptanzkriterien:**
  - [ ] Alle Objekte werden in übersichtlicher Liste angezeigt
  - [ ] Status-Filter (Draft/Published/Archived) funktioniert
  - [ ] Quick-Actions für Erstellen, Bearbeiten, Exportieren
  - [ ] Responsive Design für Mobile/Desktop
- **Aufwand:** 5 Story Points
- **Abhängigkeiten:** Property-Liste, Auth-System

### F-004: PDF Export (Dokumente)
- **Status:** Draft
- **Priorität:** Must Have
- **Spec:** [04-pdf-export.md](04-pdf-export.md)
- **Beschreibung:** Export von Typenschein und Exposé als PDF/HTML
- **Akzeptanzkriterien:**
  - [ ] Typenschein wird als einseitiges PDF generiert
  - [ ] Exposé wird als mehrseitiges PDF generiert
  - [ ] Export ohne manuelle Nachbearbeitung verwendbar
  - [ ] Async-Processing mit Status-Updates
- **Aufwand:** 8 Story Points
- **Abhängigkeiten:** Export-Engine, Templates

---

## Epic 2: Operating Costs & Analysis

### F-005: Operating Costs Input
- **Status:** Not Started
- **Priorität:** Must Have
- **Spec:** [05-operating-costs.md](05-operating-costs.md)
- **Beschreibung:** Eingabe und Verwaltung monatlicher Betriebskosten
- **Akzeptanzkriterien:**
  - [ ] Alle Standard-Kostenkategorien sind verfügbar
  - [ ] Berechnung der Gesamtkosten erfolgt automatisch
  - [ ] Perioden (monatlich/vierteljährlich/jährlich) werden unterstützt
  - [ ] Validierung verhindert negative Werte
- **Aufwand:** 5 Story Points
- **Abhängigkeiten:** Property-System, Kosten-Schema

### F-006: Community Cost Comparison
- **Status:** Not Started
- **Priorität:** Should Have
- **Spec:** [06-cost-comparison.md](06-cost-comparison.md)
- **Beschreibung:** Vergleich eigener Betriebskosten mit Community-Schnitt
- **Akzeptanzkriterien:**
  - [ ] Abweichung wird in € und % angezeigt
  - [ ] Community-Schnitt wird für alle Kostenkategorien berechnet
  - [ ] Mindestens n=10 Datensätze pro Region erforderlich
  - [ ] Kosten pro m² werden berücksichtigt
- **Aufwand:** 8 Story Points
- **Abhängigkeiten:** Operating Costs, Community-Stats

---

## Epic 3: Advanced Features (v1.1+)

### F-007: SAS 360 (Portfolio-Vergleich)
- **Status:** Not Started
- **Priorität:** Should Have
- **Spec:** [07-sas360.md](07-sas360.md)
- **Beschreibung:** Vergleich mehrerer eigener Objekte mit Kennzahlen
- **Akzeptanzkriterien:**
  - [ ] Mindestens 3 Objekte können verglichen werden
  - [ ] Sortierung und Filterung funktioniert reaktiv
  - [ ] Kennzahlen werden als Tabelle und Charts dargestellt
  - [ ] Export der Vergleichsdaten ist möglich
- **Aufwand:** 13 Story Points
- **Abhängigkeiten:** Property-System, Chart-Engine

### F-008: Enhanced Exposé Templates
- **Status:** Not Started
- **Priorität:** Could Have
- **Spec:** [08-expose-templates.md](08-expose-templates.md)
- **Beschreibung:** Verschiedene Exposé-Layouts und Stile
- **Akzeptanzkriterien:**
  - [ ] Mindestens 3 verschiedene Templates verfügbar
  - [ ] Stil reicht von neutral bis emotional
  - [ ] Branding kann angepasst werden
  - [ ] Vorschau vor Export ist verfügbar
- **Aufwand:** 8 Story Points
- **Abhängigkeiten:** PDF Export, Template-System

---

## Epic 4: Platform Features (v2+)

### F-009: Service Provider Ratings
- **Status:** Not Started
- **Priorität:** Could Have
- **Spec:** [09-service-ratings.md](09-service-ratings.md)
- **Beschreibung:** Bewertung von Gutachtern, Anwälten, Handwerkern
- **Akzeptanzkriterien:**
  - [ ] CRUD für Bewertungen funktioniert
  - [ ] Moderation verhindert Missbrauch
  - [ ] Aggregation zu Durchschnittsbewertungen
  - [ ] Verbindung zu Immobilienprojekten möglich
- **Aufwand:** 13 Story Points
- **Abhängigkeiten:** Rating-System, Moderation

### F-010: Market Trends & Analytics
- **Status:** Not Started
- **Priorität:** Won't Have (v3)
- **Spec:** [10-market-trends.md](10-market-trends.md)
- **Beschreibung:** Zeitreihen-Analyse und Marktentwicklungen
- **Akzeptanzkriterien:**
  - [ ] Preisentwicklungen werden über Zeit dargestellt
  - [ ] Regionale Trends werden identifiziert
  - [ ] Prognosen basieren auf historischen Daten
  - [ ] Export der Trend-Daten möglich
- **Aufwand:** 21 Story Points
- **Abhängigkeiten:** Historische Daten, ML-Engine

---

## Feature-Matrix

| Feature | Epic | MoSCoW | Status | Story Points | Abhängigkeiten |
|---------|------|---------|---------|--------------|----------------|
| F-001 | Core | Must | Draft | 8 | Datenmodell, Auth |
| F-002 | Core | Must | Draft | 13 | Community-Stats, Charts |
| F-003 | Core | Should | Draft | 5 | Property-Liste, Auth |
| F-004 | Core | Must | Draft | 8 | Export-Engine, Templates |
| F-005 | Costs | Must | Not Started | 5 | Property-System, Schema |
| F-006 | Costs | Should | Not Started | 8 | Operating Costs, Community |
| F-007 | Advanced | Should | Not Started | 13 | Property-System, Charts |
| F-008 | Advanced | Could | Not Started | 8 | PDF Export, Templates |
| F-009 | Platform | Could | Not Started | 13 | Rating-System, Moderation |
| F-010 | Platform | Won't | Not Started | 21 | Historische Daten, ML |

---

## Roadmap & Releases

### **v1.0 (MVP) - Q2 2024**
**Must Have Features:**
- F-001: FlatForm (Typenschein-Erfassung)
- F-002: Normal Distribution (Community-Vergleich)
- F-004: PDF Export (Dokumente)
- F-005: Operating Costs Input

**Ziel:** Funktionsfähiger Typenschein mit Community-Vergleich

### **v1.1 (Enhanced) - Q3 2024**
**Should Have Features:**
- F-003: Dashboard (Übersicht)
- F-006: Community Cost Comparison
- F-007: SAS 360 (Portfolio-Vergleich)

**Ziel:** Vollständige Immobilienverwaltung mit Analyse

### **v2.0 (Platform) - Q4 2024**
**Could Have Features:**
- F-008: Enhanced Exposé Templates
- F-009: Service Provider Ratings

**Ziel:** Erweiterte Plattform-Funktionalität

---

## Technische Abhängigkeiten

### **Frontend Components**
- Form-Wizard für Typenschein-Erfassung
- Chart-Engine für Normalverteilung
- PDF-Generator für Exports
- Dashboard-Framework

### **Backend Services**
- Property-Management API
- Community-Stats Aggregation
- Export-Processing Queue
- Analytics & Tracking

### **Infrastructure**
- Supabase (Auth, Database, Storage)
- Redis für Caching
- Queue-System für Exports
- Monitoring & Logging

---

## Nächste Schritte

### **Sprint 1-2 (Wochen 1-4)**
1. **F-001: FlatForm** - Basis-Formular mit Validierung
2. **F-005: Operating Costs** - Kosten-Eingabe-System
3. **Datenmodell** - Supabase-Schema aufsetzen

### **Sprint 3-4 (Wochen 5-8)**
1. **F-002: Normal Distribution** - Community-Vergleich
2. **F-004: PDF Export** - Basis-Export-Funktionalität
3. **F-003: Dashboard** - Übersichts-Interface

### **Sprint 5-6 (Wochen 9-12)**
1. **F-006: Community Cost Comparison** - Kosten-Vergleich
2. **F-007: SAS 360** - Portfolio-Analyse
3. **Testing & Bugfixes** - Qualitätssicherung

---

## Definition of Done

Ein Feature gilt als "Done", wenn:
- [ ] Alle Akzeptanzkriterien erfüllt sind
- [ ] Code-Review abgeschlossen ist
- [ ] Unit-Tests geschrieben und bestanden sind
- [ ] Integration-Tests bestanden sind
- [ ] Dokumentation aktualisiert ist
- [ ] Feature-Flag aktiviert ist (falls relevant)
- [ ] Performance-Kriterien erfüllt sind
- [ ] Accessibility-Standards eingehalten werden