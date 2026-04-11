---
title: "TeamChef"
type: project
status: active
created: 2026-04-09
updated: 2026-04-11
tags: [teamchef, sports, rating, gamification, webdev]
confidence: medium
aliases: [teamchef, TeamChef]
family: _teamchef-skiller
---

# TeamChef

## Summary

TeamChef ist eine Community-basierte Sportbewertungsplattform mit Fußball als wahrscheinlichem Startmarkt. Nutzer bewerten Teams oder Spieler nach wenigen Kriterien und werden dafür belohnt, wenn ihre Einschätzungen nahe am kollektiven Durchschnitt liegen.

Siehe [[_teamchef-skiller]] für den vollständigen Bewertungsmodell- und Skiller-Kern.

## Produktkern

- Community bewertet Spieler oder Teams nach wenigen Kriterien
- System berechnet Durchschnitt und individuelle Abweichung
- Punkte, Ranglisten und Belohnungen schaffen Wettbewerb
- Trainer- und Teamfeedback könnte ein zweiter Nutzungsmodus werden
- mittelfristig zusätzliche Rollen: Vereine, Sponsoren, weitere Sportarten

## Spannungen im Material

- Fußballfokus vs. generische Multisport-Plattform
- Feedback-Tool vs. Spiel/Gamification-Produkt
- Community-Plattform vs. Scouting- oder Talentlogik
- `TeamChef` als Name vs. Alternativen wie `Skillers.app` oder `SKILLER`
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
- später: Streuung/Standardabweichung als Signal für Konsistenz oder Uneinigkeit
- perspektivisch: Perzentile oder Z-Werte statt nur Rohranking
- operative Idee: Bewertungen bis Tagesende sammeln, dann nächtliche Auswertung

## Informationsarchitektur und UX

- Mobiler, schrittweiser Bewertungsflow (QCard-Flow) — siehe [[_teamchef-skiller]]
- Dashboard dient als Startpunkt und Rücksprungziel
- Sehr kurze Aufgabenpfade, gegen überladenes Social-Produkt im MVP

## Datenmodell-Richtung

- Kernentitäten: `Users`, `Teams`, `Players`, `Matches`, `Ratings`, `Ranking`, `Notifications`
- Zweistufige Speicherung: Detailbewertungen pro Match + aggregierte Verlaufsdaten für Saisonhistorie
- Offene Implementationsfrage: feste Bewertungsspalten vs. flexiblere JSON-/Key-Value-Struktur
- Aktuelles Testbild: `tbl_rating` mit 5 Skill-Spalten plus `total` und `avg`

## MVP-Plan (Stand 2026-04)

Aus [[teamchef-mvp-dialog]]:

- **Tech-Basis**: WordPress + „Calculated Fields Form"-Plugin als schnellster Validierungsweg
- **Datenmodell**: `Users`, `Teams`, `Players`, `Matches`, `Ratings`, `Ranking`, `Notifications`
- **Logik**: User bewertet → System berechnet Community-Durchschnitt → User-Score = Nähe zum Durchschnitt → Leaderboard
- **Upgrade-Pfad**: eigener Stack bleibt offen, sobald die Kernlogik sich bewährt

## Daten

- `raw/data/wc2026_matches_dewiki.json` — WC2026-Spielplan (aus dewiki), als Match-Datenbasis vorgesehen
- [[eu-football-clubs-research]] — Größenordnung potenzieller Vereinsbasis in der EU

## Nächste Schritte

- Benennung TeamChef vs. alternative Naming-Ideen konsolidieren
- MVP hart gegen Vision abgrenzen
- Bewertungslogik und Trust-/Abuse-Risiken schärfen
- Rohmaterial weiter in stabile Themen- und Vergleichsseiten überführen

## Quellen

- [[teamchef-skiller-dialogs]]
- [[teamchef-mvp-dialog]]
- [[_source-migration]]
- [[eu-football-clubs-research]]
- [[wc2026-matches-dewiki]]

## Verwandte Seiten

- [[_teamchef-skiller]]
- [[teamchef-v0/overview]]
- [[questions]]
- [[_raw-structure]]
