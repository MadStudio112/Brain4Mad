# Use Cases – FlatRace

## Übersicht
Dieses Dokument beschreibt die wichtigsten Anwendungsfälle von FlatRace aus Nutzerperspektive. Die Use Cases sind nach User Journey und Priorität geordnet.

## Primäre User Journeys

### UC-001: Typenschein erstellen (Core Journey)
**Beschreibung:** Ein Nutzer möchte ein standardisiertes Datenblatt für seine Immobilie erstellen, um eine objektive Bewertung zu erhalten.

**Primäre Akteure:**
- Private Eigentümer:innen
- Makler:innen
- Vermieter:innen

**Vorbedingungen:**
- Nutzer ist angemeldet
- Immobilie existiert physisch

**Hauptszenario:**
1. Nutzer meldet sich an und wählt "Neues Objekt erstellen"
2. System führt durch schrittweisen Wizard:
   - Grunddaten eingeben (Adresse, Größe, Zimmer)
   - Ausstattung beschreiben (Energie, Zustand, Ausstattung)
   - Betriebskosten erfassen
3. System validiert Eingaben und zeigt Live-Vorschau
4. Nutzer speichert Typenschein
5. System generiert Community-Vergleich automatisch

**Alternativszenarien:**
- **UC-001a:** Nutzer bricht Erfassung ab und speichert als Draft
- **UC-001b:** System erkennt unvollständige Daten und zeigt Warnungen

**Erfolgskriterien:**
- Typenschein ist in < 2 Minuten erstellt
- Alle Pflichtfelder sind ausgefüllt und validiert
- Community-Vergleich ist verfügbar

**Nachbedingungen:**
- Typenschein ist gespeichert und kann exportiert werden
- Community-Statistiken sind aktualisiert

---

### UC-002: Immobilie bewerten (Analysis Journey)
**Beschreibung:** Ein Nutzer möchte seine Immobilie objektiv bewerten und mit dem Markt vergleichen.

**Primäre Akteure:**
- Eigentümer:innen
- Käufer:innen
- Investoren

**Vorbedingungen:**
- Typenschein existiert
- Community-Daten sind verfügbar

**Hauptszenario:**
1. Nutzer öffnet Typenschein
2. System zeigt Normalverteilung für alle Kennzahlen
3. Nutzer sieht Position seiner Immobilie (über/unter Durchschnitt)
4. System berechnet Z-Score und Percentile
5. Nutzer kann einzelne Metriken detailliert analysieren

**Alternativszenarien:**
- **UC-002a:** Wenige Community-Daten verfügbar → aggregierte Werte aus größerer Region
- **UC-002b:** Nutzer filtert nach spezifischen Kriterien (Baujahr, Größe)

**Erfolgskriterien:**
- Vergleichswerte für ≥80% der Metriken verfügbar
- Position klar als "über/unter Durchschnitt" kommuniziert
- Ladezeit < 300ms

---

### UC-003: Betriebskosten analysieren (Cost Journey)
**Beschreibung:** Ein Nutzer möchte die Wirtschaftlichkeit seiner Immobilie anhand der Betriebskosten bewerten.

**Primäre Akteure:**
- Vermieter:innen
- Eigentümer:innen
- Verwalter:innen

**Vorbedingungen:**
- Typenschein mit Betriebskosten existiert
- Community-Daten für Region verfügbar

**Hauptszenario:**
1. Nutzer öffnet Betriebskosten-Bereich
2. System zeigt Kostenübersicht nach Kategorien
3. Nutzer sieht Vergleich mit Community-Schnitt
4. System berechnet Abweichungen in € und %
5. Nutzer identifiziert Optimierungspotenziale

**Alternativszenarien:**
- **UC-003a:** Kosten werden quartalsweise erfasst
- **UC-003b:** Nutzer teilt Kosten mit anderen (z.B. Nebenkostenabrechnung)

**Erfolgskriterien:**
- Alle Kosten korrekt summiert
- Community-Vergleich für alle Kategorien verfügbar
- Abweichungen klar dargestellt

---

### UC-004: Dokumente exportieren (Export Journey)
**Beschreibung:** Ein Nutzer möchte professionelle Dokumente für die Vermarktung oder Dokumentation erstellen.

**Primäre Akteure:**
- Makler:innen
- Eigentümer:innen
- Verwalter:innen

**Vorbedingungen:**
- Typenschein ist vollständig
- Export-System ist verfügbar

**Hauptszenario:**
1. Nutzer wählt Export-Option (Typenschein oder Exposé)
2. System zeigt Vorschau mit Layout-Optionen
3. Nutzer konfiguriert Branding und Sprache
4. System generiert PDF/HTML async
5. Nutzer erhält Download-Link per E-Mail

**Alternativszenarien:**
- **UC-004a:** Batch-Export mehrerer Objekte
- **UC-004b:** Integration mit CRM-System (z.B. Immobiliensoftware)

**Erfolgskriterien:**
- Export ohne manuelle Nachbearbeitung verwendbar
- Branding anpassbar
- Async-Processing mit Status-Updates

---

### UC-005: Portfolio verwalten (Management Journey)
**Beschreibung:** Ein Nutzer möchte mehrere Immobilien verwalten und vergleichen.

**Primäre Akteure:**
- Mehrfach-Eigentümer:innen
- Investoren
- Verwalter:innen

**Vorbedingungen:**
- Mehrere Typenscheine existieren
- Dashboard ist verfügbar

**Hauptszenario:**
1. Nutzer öffnet Portfolio-Übersicht
2. System zeigt alle Objekte mit KPIs
3. Nutzer filtert und sortiert nach Kriterien
4. System erstellt Vergleichsanalyse (SAS 360)
5. Nutzer exportiert Portfolio-Bericht

**Alternativszenarien:**
- **UC-005a:** Nutzer gruppiert Objekte nach Typ (Miete/Kauf)
- **UC-005b:** Performance-Monitoring über Zeit

**Erfolgskriterien:**
- Mindestens 3 Objekte vergleichbar
- Filterung und Sortierung funktionieren reaktiv
- Export der Vergleichsdaten möglich

---

## Sekundäre Use Cases

### UC-006: Community-Daten beitragen
**Beschreibung:** Nutzer tragen durch ihre Eingaben zur Verbesserung der Community-Daten bei.

**Primäre Akteure:** Alle Nutzer

**Hauptszenario:**
1. Nutzer erstellt Typenschein
2. System anonymisiert Daten für Community-Stats
3. Community-Vergleichswerte werden genauer
4. Nutzer profitiert von verbesserten Vergleichswerten

### UC-007: Marktentwicklung beobachten
**Beschreibung:** Nutzer möchte Trends in seiner Region beobachten.

**Primäre Akteure:** Investoren, Makler

**Hauptszenario:**
1. Nutzer analysiert historische Community-Daten
2. System zeigt Entwicklung über Zeit
3. Nutzer identifiziert Markttrends
4. System erstellt Trend-Bericht

---

## Use Case Priorisierung

### **High Priority (v1 MVP)**
- UC-001: Typenschein erstellen
- UC-002: Immobilie bewerten
- UC-003: Betriebskosten analysieren
- UC-004: Dokumente exportieren

### **Medium Priority (v1.1)**
- UC-005: Portfolio verwalten

### **Low Priority (v2+)**
- UC-006: Community-Daten beitragen
- UC-007: Marktentwicklung beobachten

---

## Technische Realisierung

### **User Journey Mapping**
```
Onboarding → Typenschein erstellen → Bewerten → Exportieren → Portfolio-Management
```

### **Touchpoints**
- **Web-App:** Hauptinterface für alle Use Cases
- **Mobile:** Responsive Design für unterwegs
- **API:** Integration mit externen Systemen
- **E-Mail:** Status-Updates und Downloads

### **Performance-Ziele**
- **Time-to-Typenschein:** < 2 Minuten
- **Community-Lookup:** < 300ms
- **Export-Generierung:** < 30 Sekunden
- **Page-Load:** < 2 Sekunden

---

## Risiken & Annahmen

### **Risiken**
- **Community-Data Quality:** Zu wenig Daten für aussagekräftige Vergleiche
- **User Adoption:** Nutzer verstehen nicht den Mehrwert der Standardisierung
- **Data Privacy:** Nutzer zögern bei Dateneingabe wegen Datenschutz

### **Annahmen**
- **Market Need:** Objektive Bewertung ist wichtiger als Marketing
- **Data Volume:** Community wächst durch Netzwerkeffekte
- **Technical Feasibility:** Supabase kann Performance-Anforderungen erfüllen

---

## Erfolgsmessung

### **KPIs**
- **Completion Rate:** % der begonnenen Typenscheine, die fertiggestellt werden
- **Export Rate:** % der Typenscheine, die exportiert werden
- **Comparison Usage:** % der Nutzer, die Community-Vergleich nutzen
- **Time-to-Value:** Durchschnittliche Zeit bis zum ersten Export
