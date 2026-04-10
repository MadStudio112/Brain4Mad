---
title: "SKILLER - UI/UX QCard Flow"
type: "source"
source: "https://chatgpt.com/g/g-p-6764154d6fcc819196ae0c76045634c6-skiller/c/6829d69a-c7a8-800b-a519-90f0f02cfd71"
author:
published:
created: 2026-04-10
description: "ChatGPT ist dein KI-Chatbot für den Alltag. Führe mit der fortschrittlichsten KI Gespräche, um Ideen zu erforschen, Probleme zu lösen und schneller zu lernen."
tags:
  - "[raw"
  - "clipping]"
confidence: "low"
status: "draft"
---
Select Team Wireframes

**Select-Team Flow Wireframes**

Dieses Dokument enthält Wireframes für den gesamten Flow: „Spiel auswählen → Mannschaft auswählen → Rating → Statuskarte → Weiterbewertung/Zurück zum Dashboard“.

---

### 1\. Dashboard QCard (Spiel auswählen)

- **Interaction**: Tippen auf Listeneintrag öffnet Modal QCard „Team auswählen“.
- **UI-Element**: QCard-Schema, Slide-In aus unten.

---

### 2\. QCard: „Mannschaft auswählen“

┌───────────────────────────────────────────────┐

├───────────────────────────────────────────────┤

│ Data: │

│ ◉ Team A (z.B. Atletico Madr.) │

│ ◉ Team B (z.B. Inter Miami) │

├───────────────────────────────────────────────┤

│ Actions: │

│ \[Zurück\] \[Weiter\] │

└───────────────────────────────────────────────┘

- Auswahl via Radiobuttons.
- **Weiter** führt direkt zur Rating-QCard.

---

### 3\. QCard: „Rating abgeben“

- **Speichern** speichert matchId, teamId, userId, Skills & Rating in DB.

---

### 4\. QCard: "Statuskarte"

- **Weiter** öffnet nächste QCard für weitere Bewertungen.

---

### 5\. QCard: "Weitere Bewertungen"

┌───────────────────────────────────────────────┐

├───────────────────────────────────────────────┤

│ Data: │

│ • Schiedsrichter bewerten │

│ • Trainer bewerten │

│ • Spieler bewerten │

│ • Zurück zum Dashboard │

├───────────────────────────────────────────────┤

│ Actions: (Tap auf Eintrag öffnet jeweilige) │

│ \[Schließen\] │

└───────────────────────────────────────────────┘

- Auswahl navigiert zu entsprechenden QCard-Flow oder schließt (Dashboard).

---

### 6\. Dashboard nach Flow

- Nach Abschluss: Dashboard zeigt wieder QCard „Spiel auswählen" mit Header/Data.
- Der Rest bleibt ausgeblendet.

---

**Anmerkung zu UX:**

- Alle QCards modular als Modal/Slide-In.
- Konsistente Buttons, klare Header.
- Schnelle Rückkopplung (Statuskarte).
- Fokus auf minimalen Arbeitsschritten.

![Generiertes Bild: Sportliche App-Benutzeroberfläche](https://chatgpt.com/backend-api/estuary/content?id=file_000000003c0061f89597020065dd14f3&ts=493290&p=fs&cid=1&sig=c769f4b07d89f46ab5daf3a5f458094dda05b518a53325e80f45735edfda0a2d&v=0)