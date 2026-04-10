---
title: "TeamChef / SKILLER Dialoge"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [teamchef, skiller, source, product]
confidence: medium
---

# TeamChef / SKILLER Dialoge

## Summary

Vier relevante Rohnotizen aus `raw/_inbox/` verdichten das ältere TeamChef-/SKILLER-Material. Der Kern bleibt konsistent: eine Community-basierte Sportbewertungsplattform, bei der Fans, Trainer und teils Spieler Bewertungen abgeben, ein Ranking über Nähe zum Kollektiv entsteht und Preise als Gamification-Anreiz dienen.

## Ingested raw files

- `SKILLER - Teamchef.md`
- `SKILLER - Team-Chef App Zusammenfassung.md`
- `SKILLER - Statistik mit Normalverteilung.md`
- `SKILLER - Bewertungsplattform Projektdefinition.md`
- `SKILLER - UIUX QCard Flow.md`
- `SKILLER - ⚽ MVP Teamchef.md`

Begrenzt relevant:
- `SKILLER - Datenbanken in SKILLER.md` — weiterhin eher Leerantwort ohne nennenswerten Wissensgewinn

Technisch relevant:
- `SQL Generator - Box-Muller Normalverteilung SQL.md` — Entwicklungspfad für Testdatengenerierung, Normalverteilung pro Skill, UNIQUE-Logik, Zeitfenster pro Spiel, Chart.js/MySQL-Anbindung sowie REST-vs-GraphQL-API-Denken

## Key observations

- Naming ist weiterhin instabil: `SKILLER`, `TeamChef` und `Team-Chef` meinen denselben Produktkern.
- Das Produkt oszilliert zwischen drei Modi:
  - Fan-Spiel mit Wettbewerb und Preisen
  - Feedback-Tool für Trainer und Teams
  - Crowd-basiertes Spielerprofiling bis hin zu Scouting-Ersatz
- Die Bewertungslogik wird stärker statistisch gedacht als im ursprünglichen Brainstorming:
  - Mittelwert und Gesamtscore bleiben Kernmetriken
  - Standardabweichung/Streuung wird als Qualitäts- oder Konsistenzsignal vorgeschlagen
  - Perzentile oder Z-Werte könnten Rankings interpretierbarer machen
- Das MVP wurde konkreter operationalisiert:
  - WordPress + Calculated Fields Form als Schnellstart
  - Landingpage, Registrierung, Bewertungssystem, Rankings und Benachrichtigungen als Kernblöcke
  - QCard-Flow für die mobile Schrittführung: Spiel → Team → Rating → Status → weitere Bewertungen
- Die Datenhaltung wird zunehmend als Zwei-Ebenen-Modell gedacht:
  - Detailbewertungen pro Match für kurzfristige Berechnung
  - Aggregierte Saison- oder Verlaufswerte für Historie und Performance
  - teils auch als JSON-/Key-Value-Modell statt starrer Spaltenstruktur
- Zusätzlich wurde ein technischer Mockdaten-Pfad ausgearbeitet:
  - Box-Muller-basierte Testdatengenerierung für `tbl_rating`
  - pro Skill eigene Mittelwerte und Standardabweichungen statt nur Gesamtwert-Logik
  - Zeitfenster pro Spiel von 18:00 bis 23:59 Uhr
  - 5 Spiele mit je 100 Usern als realistisches Testsetup
  - Diskussion um `UNIQUE(user_id, game_id)` für Datenintegrität
- Die Vision wurde ausgeweitet auf digitale Spielerkarten, globale Reichweite und spätere Multisport-Erweiterung.

## Useful extracted claims

### Produktbeschreibung

- Interaktive Plattform für Leistungsbewertung von Teams und Spielern
- Schwarmintelligenz als Kernmechanismus für objektivere Einschätzung
- Transparenz durch öffentliche oder nachvollziehbare Bewertungsresultate
- Spieler können als digitale Leistungsprofile bzw. Karten dargestellt werden

### Zielgruppen

- Fans als aktive Bewertende und Spielteilnehmer
- Trainer als Empfänger strukturierter Rückmeldungen zu Spiel und Training
- Teams/Vereine als Präsentations- und Feedbackobjekte
- später auch Sponsoren, Verbände und andere Sportarten

### Mechanik

- Bewertung über definierte Kriterien
- Ranking nach Nähe zum Gemeinschaftswert
- Preise oder Belohnungen als Incentive
- mögliche Erweiterung um Perzentil, Z-Wert oder Streuung statt nur Summe und Durchschnitt
- Bewertungsfenster bis Spielende bzw. Tagesende, danach nächtliche Auswertung per Cron-Job

### UX- und MVP-Hinweise

- Mobile QCard-/Modal-Logik für einen sehr kurzen Bewertungsflow
- Dashboard als Einstieg in Spielauswahl und Folgeaktionen
- Statuskarte direkt nach dem Absenden als schnelle Rückkopplung
- mögliche Folgeflows: Trainer-, Schiedsrichter- oder Spielerbewertung

### Technische Notizen aus späterem SQL/API-Dialog

- Vorhandene Testtabelle: `tbl_rating` mit `user_id`, `group_id`, `game_id`, `rating_1` bis `rating_5`, `total`, `avg`, `timestamp`
- Wichtige fachliche Korrektur: Nicht die Summe der 5 Ratings soll normalverteilt sein, sondern jeder Skill für sich
- Für Tests vorgesehen: 5 Spiele, je 100 User, jeder User bewertet jedes Spiel genau einmal
- Bewertungsfenster: pro Spiel ab 18:00 Uhr bis 23:59 Uhr, verteilt über die letzten 5 Tage
- Auswertungsidee: Schwarmurteil pro Skill aus den 100 Einzelratings, daraus objektivierte Skill-Einschätzung
- Frontend-Hinweis: Chart.js greift nicht direkt auf MySQL zu, sondern braucht Backend/API dazwischen
- API-Denken offen zwischen klassischem REST und GraphQL

## Risks and tensions

- "Objektive" Crowd-Bewertung ist nur plausibel, wenn Manipulation, Bias und Fan-Lager-Effekte abgefedert werden.
- Der Sprung von Fan-Gamification zu seriösem Trainer- oder Scouting-Tool ist nicht trivial.
- Globale Vision, Multisport und Werbepartner machen das Konzept schnell zu breit für einen MVP.

## Relationship to existing notes

Ergänzt und präzisiert:
- [[teamchef-source-migration]]
- [[teamchef]]
- [[teamchef-open-questions]]

Rohbasis liegt nach Einsortierung unter:
- `raw/notes/teamchef/skiller-dialogs/`
