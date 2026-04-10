---
title: "TeamChef MVP (Skiller-Dialog)"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [teamchef, mvp, wordpress, datenmodell]
confidence: high
---

# TeamChef MVP (Skiller-Dialog)

Quelle: `raw/notes/teamchef-mvp-dialog.md` (ChatGPT-Dialog)

## MVP-Ansatz

Das Dokument beschreibt einen **pragmatischen MVP**: WordPress als Host + "Calculated Fields Form"-Plugin für die Bewertungslogik, um ohne eigene Backend-Entwicklung in die Validierung zu kommen.

- Ziel: schnellstes UI-Feedback gegen Community-Durchschnitt
- Bewusst kein eigenes Framework, kein eigenes Hosting für die erste Iteration
- Upgrade-Pfad zu echter App bleibt offen

## Datenmodell (Kern-Entitäten)

- **Users** — Nutzerprofile, Auth
- **Teams** — Vereine/Nationalmannschaften
- **Players** — Spieler mit Teamzuordnung
- **Matches** — Spielpaarungen (Anknüpfung an `raw/data/wc2026_matches_dewiki.json`)
- **Ratings** — einzelne Bewertung eines Users zu Match/Team/Spieler
- **Ranking** — aggregierter Score / Leaderboard pro User
- **Notifications** — Ergebnis- und Event-Benachrichtigungen

## Logik (Kern)

- User bewertet nach festem Kriterienkatalog
- System berechnet Community-Durchschnitt pro Bewertungseinheit
- User-Score = Nähe zum Durchschnitt → Punkte
- Leaderboard aggregiert Punkte über Zeit

## Einordnung

Ergänzt [[teamchef]] um konkreten MVP-Plan und erstmaliges explizites Datenmodell. Bestätigt bisherige Annahmen aus [[teamchef-source-migration]] (Bewertung nahe Durchschnitt = Belohnung).

## Offen

- Wordpress-Weg tragfähig für Rollen, Leaderboards, Benachrichtigungen?
- Skalierung auf Spielertiefe (nicht nur Team)?
- Missbrauchsschutz (Bot-Bewertungen, Kollusion)?
