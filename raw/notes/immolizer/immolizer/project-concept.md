# Projektkonzept: Immobilien-Blutbild-System (international skalierbar)

## Ziel des Projekts

Eine webbasierte Anwendung zur Bewertung und Analyse von Immobilien, dargestellt in Form eines verständlichen "Blutbilds". Nutzer geben ihre Objektdaten ein, das System analysiert diese anhand von Community-Durchschnittsdaten und visualisiert die Ergebnisse als Marker entlang einer Normalverteilung.

---

## Systemkonzept

### 1. Struktur & Betrieb

- Für jedes Land wird eine eigene Instanz der Plattform betrieben (eigene Domain, Datenbank, JSON-Felddefinitionen)
- Der technische Kern (Code, Struktur) ist für alle Länder gleich
- Labels, Einheiten, Regeln und Begriffe sind in länderspezifischen JSON-Dateien organisiert

### 2. Datenerfassung & Darstellung

- Nutzer geben Daten zu ihren Immobilien ein (z. B. Stromkosten, Fläche, Kaufpreis)
- Alle Eingaben werden lokal in SQL-Datenbanken gespeichert
- Die Struktur der Felder (Label, Einheit, Gruppierung) wird dynamisch über JSON geladen
- Die Auswertung erfolgt über statistische Verfahren (z. B. Normalverteilung)
- Die Ergebnisse werden als Marker auf einer Glockenkurve visualisiert („Blutbild der Immobilie“)

### 3. Lernsystem & Markerlogik

- Jeder Vergleichswert wird als Marker auf einer statistischen Verteilung dargestellt
- Marker zeigen, ob der eingegebene Wert im normalen Bereich liegt oder stark abweicht
- Das System lernt mit jeder Eingabe und verfeinert Mittelwert, Streuung und Trends
- Ziel ist eine dynamische, selbsterklärende Übersicht über den „Zustand“ der Immobilie

### 4. Zentrale Auswertung (späterer Schritt)

- In regelmäßigen Intervallen werden anonymisierte Daten aus den Länderinstanzen exportiert
- Diese Daten fließen in ein zentrales Analyse-System ein
- Ziel: weltweite Vergleichbarkeit, Heatmaps, Marktverläufe, automatisierte Benchmarks
