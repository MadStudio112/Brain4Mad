---
title: ".env Variablen"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [openclaw, config, env, secrets]
confidence: low
---

# .env

Secrets-Datei unter `C:\Users\Mad\.openclaw\.env`. **Werte nie hier dokumentieren.**
Template: `C:\Users\Mad\.openclaw\.env.example`.

## Bekannte Variablen-Gruppen (aus [[../../../openclaw/overview]] und BRAIN.md)

| Gruppe | Beispiel-Vars (nur Namen) | Zweck |
|---|---|---|
| GitHub | `GITHUB_TOKEN` o.ä. | gh-CLI + SSH Auth |
| Google OAuth2 | `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`, Refresh-Tokens | Gmail API, Drive API, Calendar API |
| Gmail SMTP | `SMTP_USER`, `SMTP_PASS` | Mail-Versand |
| Notion | `NOTION_API_KEY` | Notion-API Zugriff |

Konto für Google-Dienste: `mad.coo.agent@gmail.com`.

## Regeln

- Werte **niemals** in Brain4Mad committen — dieser Vault ist git-synchronisiert.
- Nur Variablennamen, Bedeutung, Status dokumentieren.
- Status-Check: `check-apis.ps1` im Runtime-Ordner.

## Status (Stand BRAIN.md 2026-03-16)

Alle o.g. APIs verifiziert. Nicht automatisch aktualisieren — Status manuell aus der
Runtime prüfen, wenn relevant.
