---
title: "ImmoSkill offene Fragen"
type: question
status: active
created: 2026-04-11
updated: 2026-04-11
tags: [immoskill, questions, proptech, ai]
confidence: low
aliases: [immoskill-open-questions]
---

# ImmoSkill offene Fragen

## Produkt-Positionierung

- Eigenständiges Produkt, Modul von [[immolizer]] oder Sub-Marke unter gemeinsamer Dachmarke?
- Zielgruppe: Eigentümer, Vermieter, Versicherer oder Verwalter? Wer hat den stärksten Pull?
- Abgrenzung zu bestehenden Versicherer-Hausrat-Apps — eigenständiger Wert oder Commodity?

## MVP-Scope

- Was gehört konkret in Version 1? Foto-Flow + Raumbuch + Objektliste reichen, oder muss Bewertung/Versicherungsexport schon mit?
- Quick Mode vs. Detail Mode — beides von Start an, oder erst Quick, dann Detail?
- Welche Objektarten zuerst (nur Wohnung, oder auch Haus + Grundstück)?
- Killer-Idee „Raum entsteht durch Fotos" — MVP-tauglich oder Post-MVP-Feature?

## AI-Scope

- Welche Erkennungen sind mit Standard-Vision-Modellen realistisch und MVP-relevant (Raumtyp, Objekt, Kategorie, Zustand, Marke, Preisbereich)?
- Confidence-Schwellen: ab wann Auto-Accept, ab wann nur Vorschlag, ab wann stille Ablehnung?
- On-device vs. Cloud-Inference — Datenschutz, Kosten, Latenz?
- Fallback, wenn AI daneben liegt: wie viele Klicks bis zur manuellen Korrektur?

## Datenmodell

- Foto als Beziehungs-Knoten: wie werden Mehrfachzuordnungen (ein Foto → mehrere Objekte) sauber modelliert?
- Konfliktauflösung bei widersprüchlichen AI-Ergebnissen über Zeit (Zustand hat sich geändert vs. falsch erkannt)?
- Zeitachse und Versionierung: Vorher/Nachher-Vergleich auf Foto-, Objekt- oder Raum-Ebene?
- Verhältnis zu Immolizer-Datenmodell — getrennte Stores oder gemeinsamer Graph?

## Monetarisierung

- Freemium vs. Abo vs. B2B-Lizenz an Versicherer?
- Preis-Ankerpunkt: Hausrat-App (niedrig), Immobilienbewertung (hoch), Inventarsoftware (mittel)?

## Relevante Seiten

- [[immoskill]]
- [[immoskill-brainstorming]]
- [[immolizer]] — möglicher Dach-/Schwester-Kontext
