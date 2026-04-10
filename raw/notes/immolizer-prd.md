


## Einleitung
**Immolizer** ist eine Plattform zur einfachen Erfassung, Verwaltung und Einordnung von Immobiliendaten. Ziel ist es, harte Fakten einer Immobilie strukturiert zu erfassen und diese verständlich mit Vergleichswerten aus einer Datenbank darzustellen. Der Fokus liegt auf Klarheit, Vergleichbarkeit und schneller Orientierung – nicht auf klassischer Immobilienvermittlung.

## Hauptziele
- Niederschwelliger Einstieg in die Immobilienbewertung
- Klare Einordnung der eigenen Immobilie im Vergleich zum Durchschnitt
- Visuelle, leicht verständliche Darstellung von Abweichungen (unter / über Durchschnitt)
- Skalierbare Basis für weiterführende Analysen und Monetarisierung

## Grundlegende Funktionalität

### 1. Onboarding der Immobilie
Im Onboarding werden **5–10 zentrale Hard Facts** abgefragt, ohne Nutzer zu überfordern.

Beispielhafte Kernangaben:
- Objekttyp (Wohnung, Haus, Grundstück)
- Untertyp (z. B. Einfamilienhaus, Mehrfamilienhaus, Gartenwohnung)
- Lage (max. Bezirk, keine Adresse)
- Wohnnutzfläche / Grundstücksfläche
- Energiekennwert (z. B. HWB)
- Land (z. B. Österreich)

Nach Abschluss des Onboardings gelangt der Nutzer direkt ins Dashboard.

### 2. Dashboard
Das Dashboard ist die zentrale Arbeitsoberfläche.

- Darstellung der eingegebenen Immobiliendaten
- Vergleich mit aggregierten Daten aus der Datenbank
- Durchschnitt, Minimum und Maximum werden berechnet
- Visualisierung über Widgets (z. B. Slider, Progressbar, Balken)
- Jeder Wert kann:
  - angezeigt
  - bearbeitet
  - gelöscht
  - neu eingegeben werden

Funktional entspricht das System einer Finanz- oder Tracking-App:  
Daten rein → Auswertung aktualisiert sich automatisch.

### 3. Vergleich & Ranking
- Jeder Hard Fact wird relativ zur Datenbank eingeordnet
- Abweichungen vom Durchschnitt werden klar sichtbar
- Langfristig: Zusammenführung aller Werte zu einem Ranking / Score  
  (Bewertungslogik und Algorithmus werden separat definiert)

### 4. Widgets
- Jedes Hard Fact ist ein eigenes Widget
- Widget zeigt:
  - aktuellen Wert
  - Vergleich zum Durchschnitt
- Klick öffnet ein Popup mit vorausgefülltem Wert zur schnellen Anpassung
- Wiederverwendbares Prinzip für Fläche, Kosten, Energie, etc.

### 5. Nutzungsmodelle
- **Free-Modus**
  - Basisfunktionen
  - eingeschränkte Datentiefe
  - kurze Werbe- oder Lade-Einblendungen zwischen Aktionen
- **Upgrade / Paid-Modus**
  - mehr Eingabemöglichkeiten
  - mehr Auswertungen
  - keine Werbung
  - stattdessen dezente Produkt- oder Dienstleistungsempfehlungen

## User Stories (Auswahl)

- **Als Nutzer** möchte ich grundlegende Immobiliendaten eingeben, damit ich sehe, wie meine Immobilie im Vergleich zum Durchschnitt steht.
- **Als Nutzer** möchte ich auf dem Dashboard alle Werte bearbeiten können, um meine Daten aktuell zu halten.
- **Als Free-User** möchte ich die Basisfunktionen kostenlos nutzen können, auch wenn Werbung eingeblendet wird.
- **Als zahlender Nutzer** möchte ich mehr Daten eingeben und detailliertere Auswertungen erhalten, ohne durch Werbung unterbrochen zu werden.

---

**Status:** Basis-PRD  
**Nächste Schritte:** Feature-Detaildefinition → User Stories je Feature → Zeit- & Aufwandsschätzung