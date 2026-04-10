# Feature-Entwicklung – Grundgerüst (Kochbuch)

Dieses Dokument dient als **verbindliche Vorlage** für die Entwicklung neuer Features. Es wird bei jedem Feature **vollständig** ausgefüllt und ist die Grundlage für Design, Entwicklung und QA.

---

## 1. Ziel des Features

**Problem / Nutzen**  
Welches konkrete Nutzerproblem wird gelöst? Warum braucht der User dieses Feature?

**Business-Ziel**  
Welchen messbaren Mehrwert bringt das Feature (Retention, Engagement, Monetarisierung, Datengewinn)?

**Erfolgskriterien (KPIs)**  
Woran erkennen wir, dass das Feature funktioniert?
- z. B. Nutzungsrate
- z. B. Abschlussrate
- z. B. Wiederkehrende Nutzung

---

## 2. User Flow

**Entry Point**  
Wo startet der User (Dashboard, Deep Link, Notification)?

**Schritte (Happy Path)**  
1. User öffnet …
2. User wählt …
3. System lädt …
4. User interagiert mit …
5. System berechnet / reagiert …
6. Ergebnis wird angezeigt

**Alternative Flows / Edge Cases**  
- Fehlende Daten
- Ungültige Eingaben
- Abbruch durch User

**Exit Points**  
- Weiterführende Aktion
- Zurück zum Dashboard

---

## 3. User Story / User Stories

**Primäre User Story**  
> Als **[User-Typ]** möchte ich **[Aktion]**, um **[Nutzen]**.

**Akzeptanzkriterien**  
- [ ] Story ist erfüllt, wenn …
- [ ] Story ist nicht erfüllt, wenn …

**Sekundäre Stories (optional)**  
- Admin / Power User / System

---

## 4. Anforderungen an Eingaben und Daten

### Eingaben (User Input)
- Feldname
- Datentyp (Number, String, Enum)
- Pflichtfeld (Ja/Nein)
- Default-Wert
- Validierungsregeln

### Systemdaten
- Datenquelle (DB, API, Cache)
- Durchschnittswerte / Benchmarks
- Aktualisierungsfrequenz

### Datenmodell (vereinfacht)
- User
- Objekt / Entity
- Messwerte

---

## 5. Berechnung / Logik

**Trigger**  
Wann wird gerechnet? (onChange, onSubmit, automatisch)

**Berechnungslogik**  
- Formel / Regelwerk
- Vergleichswerte
- Normalisierung / Gewichtung

**Ergebnis-Typen**  
- Absoluter Wert
- Differenz zum Durchschnitt
- Score / Ranking

---

## 6. UI-Komponenten (für Entwicklung relevant)

- Eingabefelder
- Slider / Selector
- Ergebnisanzeige
- Visualisierung (Chart, Badge, Ranking)

---

## 7. Nicht-Ziele / Out of Scope

Was gehört **bewusst nicht** zu diesem Feature?

---

## 8. Abhängigkeiten & Risiken

- Technische Abhängigkeiten
- Datenqualität
- Performance

---

## 9. Offene Fragen

- Noch zu klären vor Umsetzung

---

## 10. Übergabe an Entwicklung

**Status**: Draft / Ready / In Umsetzung  
**Owner**:  
**Datum**:

