# MVP

## Projektname: **TEAMCHEF – Die Fußball-Kompetenz-Plattform**

## **1. Ziel des MVP**

Ein interaktives Bewertungstool für Fußballspiele und -spieler, das durch Community-Durchschnitt und Gamification Wettbewerb erzeugt. Ziel ist es, möglichst genau die kollektive Bewertung vorherzusagen und damit zu gewinnen.

---

## **2. Zielgruppen**

- Fußballfans (aktive Zuschauer, Community-User)
- Spieler & Trainer (Feedback zur Leistung)
- Vereine (Talent- & Teamanalyse)
- Amateur- & Jugendmannschaften

---

## **3. Zentrale MVP-Funktionen**

### **A. Bewertungssystem**

- Nutzer können nach einem Spiel **Spieler und/oder Teams bewerten**
- Bewertung über **Slider (z. B. 1–10 Punkte)** oder **Sterne/Buttons**
- **Fünf Kategorien**: Einsatz, Technik, Teamplay, Spielstärke, Siegeswille

### **B. Community-Durchschnitt & Game-Mechanik**

- Nach Abgabe der Bewertung sieht der User, **wie nahe seine Einschätzung am Durchschnitt** der Community liegt
- Je näher an der Community – desto mehr Punkte

### **C. Rangliste & Spiel**

- **Leaderboard**, wer aktuell am genauesten trifft (nach Spiel, Woche, Saison)
- Evtl. „Level-Aufstieg“ oder Abzeichen
- Punkte für richtige Einschätzungen
- Optionale Preise oder Belohnungen (virtuell oder real)

### **D. Nutzerprofil**

- Registrierung/Login
- Anzeige von:
  - Eigene Bewertungen
  - Erfolgsquote (Treffgenauigkeit)
  - Position im Leaderboard
  - Trophäen/Badges

---

## **4. Technische Anforderungen MVP**

- **CMS**: ClassicPress als Basis
- **Frontend**: React (Vanilla JS, kein TypeScript, keine komplexen Frameworks)
- **Integration**: React-Komponenten werden in ClassicPress-Seiten eingebettet (z. B. via Shortcode oder Custom Template)
- **Sprache & Hosting**:
  - Je Land eine eigene Instanz (z. B. teamchef.at, teamchef.de)
  - Inhalte, UI und Spiele werden **in der Landessprache ausgegeben**
- **Datenstruktur**: JSON-basiert, später in MySQL-Tabellen überführt
- **Datenbank**: Spieler, Teams, Bewertungen, User, Bewertungen-Log, Punktestand
- **Gamification Engine**: einfache Vergleichslogik Bewertung vs. Durchschnitt

---

## **5. Erweiterbare Sektionen (nicht MVP-kritisch, aber vorbereitbar)**

- Foren & Diskussionen (Community-Interaktion)
- Trainer-Zugänge zur Analyse von Feedback
- Statistiken/Trends über längere Zeiträume
- Ranglisten nach Spieler, Teams, Liga, Nationen und Weltrangliste

---

## **6. Fokus: Was ist im MVP enthalten?**

- Team-Bewertung mit sofortigem Feedback vs. Durchschnitt
- Punktezählung & Leaderboard
- Registrierung & Profil mit Erfolgsstatistik
- Frontend-Oberfläche für Bewertung, Auswertung und Rangliste
- Automatisches Email an User, nach Ablauf der Bewertung

---

## **7. Was ist _nicht_ Teil des MVP**

- Ausgefeilte soziale Features (Chat, Forum)
- Mobile App (nur Web App)
- Vereins- oder Trainer-Dashboards
- Komplexe Admin-Tools
