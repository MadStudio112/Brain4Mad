---
title: "TeamChef / Skiller — Kern"
type: project
status: active
created: 2026-04-11
updated: 2026-04-11
tags: [teamchef, skiller, sports, rating]
confidence: medium
---

# TeamChef / Skiller — Kern

## Produktkern

Community-basierte Sportbewertungsplattform. Nutzer bewerten Teams oder Spieler nach definierten Kriterien. Punkte entstehen durch Nähe zum kollektiven Durchschnitt — nicht durch subjektiv „beste" Bewertung, sondern durch Übereinstimmung mit dem Schwarmund.

Das Konzept oszilliert zwischen drei Modi:
- Fan-Spiel mit Wettbewerb und Preisen (Gamification)
- Feedback-Tool für Trainer und Teams
- Crowd-basiertes Spielerprofiling bis hin zu Scouting-Ersatz

## Skiller-Bewertungsmodell

- Bewertung über definierte Kriterien (Skill-Spalten)
- Ranking nach Nähe zum Kollektiv-Durchschnitt
- Erweiterung geplant: Streuung/Standardabweichung als Konsistenzsignal, Perzentile/Z-Werte statt Rohranking
- Jeder Skill soll separat normalverteilt betrachtet werden — nicht nur die Gesamtsumme
- Bewertungsfenster: pro Spiel 18:00 bis 23:59 Uhr, nächtliche Auswertung per Cron-Job
- Testsetup: 5 Spiele, je 100 User, `UNIQUE(user_id, game_id)` für Datenintegrität

## QCard-Flow (UX)

Mobiler, schrittweiser Bewertungsflow:
1. Spiel wählen
2. Team wählen
3. Rating abgeben
4. Statuskarte (sofortige Rückkopplung)
5. Weitere Bewertungen

Dashboard als Startpunkt und Rücksprungziel.

## Normalverteilungs-Logik

Aus SQL-Generator-Dialog: Box-Muller-basierte Testdatengenerierung für `tbl_rating`. Pro Skill eigene Mittelwerte und Standardabweichungen. Tabelle: `tbl_rating` mit `user_id`, `group_id`, `game_id`, `rating_1`–`rating_5`, `total`, `avg`, `timestamp`.

Frontend-Hinweis: Chart.js braucht Backend/API als Zwischenschicht — kein direkter MySQL-Zugriff. API-Ansatz offen zwischen REST und GraphQL.

## Naming-Instabilität

`SKILLER`, `TeamChef` und `Team-Chef` meinen denselben Produktkern. Entscheidung steht aus: `TeamChef` (Community-Fokus) vs. `SKILLER` (Marktfähigkeit/Positionierung).

## Projektseiten

- [[teamchef/overview]]
- [[teamchef-v0/overview]]
