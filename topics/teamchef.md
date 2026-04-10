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

TeamChef ist ein Konzept für eine Community-basierte Fußball-Bewertungsplattform, bei der Nutzer Teams oder Spieler bewerten und dafür belohnt werden, wenn ihre Einschätzungen nahe am kollektiven Durchschnitt liegen.

## Produktkern

- Community bewertet Spieler oder Teams nach wenigen Kriterien
- System berechnet Durchschnitt und individuelle Abweichung
- Punkte, Ranglisten und Belohnungen schaffen Wettbewerb
- mittelfristig sind zusätzliche Rollen wie Trainer, Vereine oder weitere Sportarten denkbar

## Spannungen im Material

- Fußballfokus vs. generische Multisport-Plattform
- Feedback-Tool vs. Spiel/Gamification-Produkt
- Community-Plattform vs. Scouting- oder Talentlogik
- TeamChef als Name vs. Alternativen wie `Skillers.app`

## Wahrscheinlicher MVP-Kern

- Match- oder Teambewertung nach Spiel
- sofortiges Feedback gegen Community-Durchschnitt
- Leaderboard und Punktelogik
- Nutzerprofil und Erfolgsstatistik
- einfache Web-App statt komplexe Plattform

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
- [[teamchef-mvp-dialog]]
- [[eu-football-clubs-research]]

## Relevante Projektseite

- [[TeamChef]]
