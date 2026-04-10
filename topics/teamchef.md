---
title: "TeamChef"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-10
tags: [teamchef, sports, rating, gamification]
confidence: medium
---

# TeamChef

## Summary

TeamChef ist ein Konzept für eine Community-basierte Sportbewertungsplattform mit Fußball als wahrscheinlichem Startmarkt. Nutzer bewerten Teams oder Spieler nach wenigen Kriterien und werden dafür belohnt, wenn ihre Einschätzungen nahe am kollektiven Durchschnitt liegen.

## Produktkern

- Community bewertet Spieler oder Teams nach wenigen Kriterien
- System berechnet Durchschnitt und individuelle Abweichung
- Punkte, Ranglisten und Belohnungen schaffen Wettbewerb
- Trainer- und Teamfeedback könnte ein zweiter Nutzungsmodus werden
- mittelfristig sind zusätzliche Rollen wie Vereine, Sponsoren oder weitere Sportarten denkbar

## Präzisierungen aus späteren Dialogen

Aus [[teamchef-skiller-dialogs]]:

- Fans sollen die Nutzung teils als Spiel erleben, nicht nur als nüchternes Bewertungstool
- Trainer könnten Rückmeldungen zu Spiel und Training erhalten, also deutlich näher an echter Teamsteuerung sein
- Die Vision reicht bis zu digitalen Spielerkarten bzw. Leistungsprofilen
- Crowd-Bewertung wird teils als möglicher Ersatz oder Vorfilter für klassisches Scouting gedacht

## Spannungen im Material

- Fußballfokus vs. generische Multisport-Plattform
- Feedback-Tool vs. Spiel/Gamification-Produkt
- Community-Plattform vs. Scouting- oder Talentlogik
- TeamChef als Name vs. Alternativen wie `Skillers.app` oder `SKILLER`
- öffentliches Fan-Ranking vs. ernsthaft nutzbare Trainerdaten

## Wahrscheinlicher MVP-Kern

- Match- oder Teambewertung nach Spiel
- sofortiges Feedback gegen Community-Durchschnitt
- Leaderboard und Punktelogik
- Nutzerprofil und Erfolgsstatistik
- einfache Web-App statt komplexe Plattform
- Fan-Use-Case zuerst, Trainer-Use-Case erst nach Validierung

## Bewertungslogik

- Kernmetriken: Gesamtscore und Durchschnitt
- Ranking über Nähe zur Community-Bewertung
- später sinnvoll: Streuung/Standardabweichung als Signal für Konsistenz oder Uneinigkeit
- perspektivisch möglich: Perzentile oder Z-Werte statt nur Rohranking
- operative Idee: Bewertungen bis Tagesende sammeln, dann nächtliche Auswertung und Ranking-Update

## Informationsarchitektur und UX

- Wahrscheinlich mobiler, schrittweiser Bewertungsflow statt komplexer Seitenstruktur
- QCard-/Modal-Flow: Spiel wählen → Team wählen → Rating abgeben → Statuskarte → weitere Bewertungen
- Dashboard dient als Startpunkt und Rücksprungziel
- Das spricht für sehr kurze Aufgabenpfade und gegen ein überladenes Social-Produkt im MVP

## Datenmodell-Richtung

- Frühe Kernentitäten bleiben plausibel: `Users`, `Teams`, `Players`, `Matches`, `Ratings`, `Ranking`, `Notifications`
- Gleichzeitig gibt es eine starke Tendenz zu zweistufiger Speicherung:
  - Detailbewertungen pro Match für Berechnung und Fairnesslogik
  - aggregierte Verlaufsdaten für Saisonhistorie und schnelle Auswertung
- Offene Implementationsfrage: feste Bewertungsspalten vs. flexiblere JSON-/Key-Value-Struktur
- Aktuelles Testbild ist konkret: `tbl_rating` mit 5 Skill-Spalten plus `total` und `avg`
- Fachlich wichtiger Punkt: Jeder Skill soll separat normalverteilt betrachtet werden, nicht nur die Gesamtsumme
- Für Simulationen wurde ein Setup mit 5 Spielen, je 100 Usern und Ratingfenster 18:00 bis 23:59 Uhr über 5 Tage beschrieben

## MVP-Plan (Stand 2026-04)

Aus [[teamchef-mvp-dialog]]:

- **Tech-Basis**: WordPress + "Calculated Fields Form"-Plugin als schnellster Validierungsweg (kein eigenes Backend für Iteration 1)
- **Datenmodell**: `Users`, `Teams`, `Players`, `Matches`, `Ratings`, `Ranking`, `Notifications`
- **Logik**: User bewertet → System berechnet Community-Durchschnitt → User-Score = Nähe zum Durchschnitt → Leaderboard
- **Upgrade-Pfad**: eigener Stack bleibt offen, sobald die Kernlogik sich bewährt

## Daten

- `raw/data/wc2026_matches_dewiki.json` — WC2026-Spielplan (aus dewiki), als Match-Datenbasis für TeamChef-Bewertungen vorgesehen
- [[eu-football-clubs-research]] — Größenordnung potenzieller Vereinsbasis in der EU (DE ~23.868, FR ~11.716, BE ~4.000, NL ~2.780, AT ~2.236; 22 von 27 Ländern ohne belastbare Zahlen). Nutzbar als Scope-Proxy, nicht als Master-Datenquelle.

## Relevante Quellen

- [[teamchef-source-migration]]
- [[teamchef-skiller-dialogs]]
- [[teamchef-mvp-dialog]]
- [[eu-football-clubs-research]]

## Relevante Projektseite

- [[TeamChef]]
