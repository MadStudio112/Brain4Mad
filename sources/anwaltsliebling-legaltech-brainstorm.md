---
title: "Anwaltsliebling LegalTech Brainstorm"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [legaltech, austria, ai, source]
confidence: medium
---

# Anwaltsliebling LegalTech Brainstorm

## Summary

Mehrere Rohdialoge aus `raw/_inbox/` beschreiben zwei eng verwandte LegalTech-Richtungen: 

1. **Anwaltsliebling** als KI-gestützte Plattform für juristische Erststrukturierung und Auskunft für Laien.
2. **Anwaltstarif-/Kostenrechner** als strukturierter RATG/AHK-Rechner mit JSON-Datenbasis und zwei Nutzungsmodi.

Gemeinsamer Nenner ist ein niedrigschwelliger Zugang zu juristischer Orientierung, deutlich schneller und günstiger als klassische Erstkontakte mit Kanzleien.

## Ingested raw files

- `Anwaltstarifrechner.md`
- `Anwaltskostenberechnung.md`
- `Anwaltsliebling.md`

## Produktkern Anwaltsliebling

- Start in Österreich, später international und mehrsprachig
- MVP-Fokus auf **Erbrecht**, **Strafrecht** und **Baurecht**
- Userflow: Landingpage → Signup/Login → Payment → Onboarding → Dashboard/Chats → Dokument-Upload → strukturierte Fallanalyse
- ChatGPT-ähnliches Dashboard mit Fallhistorie, Projekten/Chats und Feedbackformular
- Backend-Idee: orchestrierte Rollen/Agenten mit domänenspezifischen Workflows, Vorlagen, Aufgaben und Prompt-Bausteinen
- Zielgruppe primär juristische Laien, sekundär später auch Anwälte als Power-User oder Intake-Empfänger

## Produktkern Anwaltskostenrechner

- Rechner für Anwaltskosten auf Basis **RATG** und **AHK**
- Kernartefakt ist eine saubere `.json`-Datenbasis aus offiziellen PDFs
- Zwei Modi wurden explizit angedacht:
  - **Mandantenmodus**: wenige Eingaben aus einer Rechnung, einfache Näherung ohne tiefen Zuschlagsdschungel
  - **Expertenmodus**: volle Parameter inkl. Zuschläge, Einheitssatz, AHK, Streitgenossen etc.
- Frontend-Idee: schlanker Rechner plus README/Doku für Entwickler

## Wichtige fachliche Punkte aus dem Kosten-Cluster

- RATG hat **TP1–TP9**, kein TP10
- AHK ergänzt RATG insbesondere in Straf- und Sonderfällen
- JSON-Datenmodell soll Position, Kurzbeschreibung, Beschreibung, Einheit und Berechnungslogik sauber abbilden
- Technische Grundlage wurde über mehrere Dialoge konkretisiert:
  - maschinenlesbare RATG/AHK-Struktur
  - README mit Quellenverweisen
  - Diskussion zu TP-Logik, Kappungen und Cap-Zonen
  - Unterscheidung zwischen RATG, AHK und fremden Tarifen wie GKTG

## Produkt- und Technikannahmen für Anwaltsliebling

- Frontend: React wurde klar bevorzugt
- UI-Library: `shadcn/ui` oder ähnlich
- Backend/Auth/Storage: Supabase
- Payment: Stripe
- Social Login: Google und Apple
- Mehrsprachigkeit: UI über Browser-/Onboarding-Sprache, Antworten dynamisch durch das Modell in der gewünschten Sprache
- Architektur: modulare Prompt-/Workflow-Struktur nach Ländern, Rechtsgebieten, Core-Files und spezialisierten Templates

## Spannungen und Risiken

- Hoher juristischer Anspruch versus klare Abgrenzung zu echter Rechtsberatung
- Internationalisierung ist attraktiv, aber für den MVP brandgefährlich breit
- Nutzer wollen einfache Antworten, die internen Workflows sind aber hochkomplex
- Für den Kostenrechner ist Quellenklarheit entscheidend, sonst wird das Ding sofort unzuverlässig

## Gute nächste Wissensobjekte

- dedizierte Topic-Seite für `[[anwaltsliebling]]`
- dedizierte Source/Topic-Seite für einen `RATG/AHK-Rechner`
- eventuell Projektordner unter `projects/legaltech/`
