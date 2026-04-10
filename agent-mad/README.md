---
title: "agent-mad — Arbeitsbereich"
type: topic
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [meta, agent]
confidence: high
---

# agent-mad

Privater Arbeitsbereich des Agents im Vault. Zwei Rollen:

## 1. Wiki-Arbeitsgedächtnis (Root-Ebene)

Laufender Kontext für die Arbeit am Brain4Mad-Wiki selbst:

- [[working-context]] — aktueller Fokus, heiße Themen, offene Schleifen
- [[project-radar]] — Kurzüberblick aller Projekte mit je einem nächsten Schritt
- [[decision-rules]] — operative Regeln für Einordnung und Wissensformen
- [[mistakes]] — wiederkehrende Fehler und Learnings
- `daily/` — Tages-Notizen
- `patterns/` — wiederverwendbare Arbeitsmuster

## 2. openclaw-Wissensbasis (`openclaw/`)

Dokumentiertes Wissen über den openclaw-Agent-Stack unter `C:\Users\Mad\.openclaw\`:
Architektur, Agents, Skills, Flows, Config, Entscheidungen, Troubleshooting. **Keine
Live-Config, keine Dumps** — die Runtime-Wahrheit bleibt in `.openclaw/`. Diese
Wissensbasis ist die verdichtete, erklärte Sicht darauf.

Einstieg: [[openclaw/overview]]

---

## Secrets-Blocklist (kritisch)

Brain4Mad liegt im git-synchronisierten **MadStudio112**-Repo. Folgende Inhalte
dürfen **nie** in `agent-mad/` (oder sonstwo in Brain4Mad) landen:

- `.env`-Werte, API-Keys, Tokens, Passwörter, OAuth-Credentials
- Inhalte aus `C:\Users\Mad\.openclaw\credentials/`
- Session-Tokens oder Auth-State
- Rohinhalte aus `C:\Users\Mad\.openclaw\exec-approvals.json`
- Logs mit PII, Chatverläufen, Medieninhalten aus `.openclaw\logs/`, `.openclaw\media/`
- SQLite-Dumps aus `.openclaw\memory/`

Erlaubt ist ausschließlich: die **Namen** von Variablen, **Struktur** von Config-Feldern
und **Zweck**-Erklärungen — ohne jegliche Werte.

Bei Zweifel: **nicht** aufschreiben.
