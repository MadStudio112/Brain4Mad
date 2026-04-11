---
title: "WM 2026 Spielplan (dewiki-Scrape)"
type: source
status: active
created: 2026-04-11
updated: 2026-04-11
tags: [teamchef, football, data, wc2026]
confidence: medium
---

# WM 2026 Spielplan (dewiki-Scrape)

Quelle: `raw/data/wc2026_matches_dewiki.json` (gescraped von `de.wikipedia.org/wiki/Fußball-Weltmeisterschaft_2026`)

## Inhalt

Strukturierter Spielplan der FIFA-Weltmeisterschaft 2026 als JSON-Array mit **104 Spielen** — dem neuen 48-Team-Format mit erstmals 12 Vorrundengruppen und einer zusätzlichen Sechzehntelfinal-Runde.

### Turnierstruktur

| Runde | Spiele |
|---|---|
| Gruppenphase (Gruppen A–L, je 6 Spiele) | 72 |
| Sechzehntelfinale | 16 |
| Achtelfinale | 8 |
| Viertelfinale | 4 |
| Halbfinale | 2 |
| Spiel um Platz 3 | 1 |
| Finale | 1 |
| **Gesamt** | **104** |

### Zeitraum & Austragungsorte

- Erstes Spiel: **2026-06-11** (Mexiko–Südafrika, Mexiko-Stadt)
- Finale: **2026-07-19**, MetLife Stadium, East Rutherford (USA)
- 16 verschiedene Austragungsstädte in den drei Gastgeberländern (USA, Mexiko, Kanada)

### Feldschema

Pro Match:
- `round`, `group` (nur Gruppenphase)
- `kickoff_local_text` (deutsche Klartext-Zeit aus dewiki)
- `kickoff_berlin_iso` / `kickoff_utc_iso` (normalisierte ISO-Timestamps)
- `venue_city`, `venue_stadium`
- `home`, `away` — für K.o.-Runden als Platzhalter-Strings (z. B. "Sieger UEFA Playoff D", "Sieger Halbfinale 1")
- `score` — noch ungespielt, durchgehend `"-:- (-:-)"` bzw. `null`
- `source` (Wikipedia-URL), `match_no` (1–104), `match_id` (`FIFA2026-M001`…`M104`)

## Einordnung

Referenzdatensatz für [[teamchef]]-Prototypen rund um reale Turnierdaten: Spielplan, Kickoff-Zeiten mit TZ-Handling, Venue-Lookup und stabile Match-IDs lassen sich direkt gegen UI- oder Bewertungs-Mockups fahren, ohne vorher einen eigenen Scraper zu bauen.

Passt thematisch zum Größenordnungs-Research aus [[eu-football-clubs-research]], ist aber **operativ** — konkreter Match-Bestand statt Vereins-Schätzwerte.

## Einschränkungen

- **Kein Master-Datensatz.** dewiki-Scrape zu einem Zeitpunkt vor Turnierstart; Teams in K.o.-Runden sind Platzhalter, Scores leer.
- `venue_stadium` für viele Gruppenspiele `null` (Wikipedia hatte zum Scrape-Zeitpunkt nur die Stadt gelistet).
- Keine Team-IDs, keine Gruppen-Tabellenlogik — nur die Match-Liste.
- Für laufende Spielstände oder finale Paarungen später gegen eine autoritative Quelle (FIFA, SofaScore, OpenFootball) nachziehen.

## Verwendung

- Mock-Daten für TeamChef-UI-Prototypen (Spielplan-Views, Kickoff-Benachrichtigungen)
- Grundlage für Bewertungs-Flow-Tests (pro Match → Spielerbewertung)
- Venue-/Zeitzonen-Testfälle im TeamChef-Datenmodell
