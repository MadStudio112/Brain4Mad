---
title: "ImmoSkill"
type: project
status: draft
created: 2026-04-10
updated: 2026-04-11
tags: [immoskill, immolizer, proptech, photo-first, ai, inventar, product, webdev]
confidence: low
aliases: [immoskill]
---

# ImmoSkill

## Summary

ImmoSkill ist ein Konzept für eine **foto-zentrierte Immobilien- und Inventarakte**. Fotos sind nicht Dokumentation, sondern **Einstiegspunkt für die Datenerfassung**. AI analysiert das Bild, schlägt Raum, Objekt, Kategorie und ggf. Marke/Preis vor, der User bestätigt mit minimalem Aufwand.

Status: frühes Brainstorming, keine MVP-Definition, kein Datenmodell, keine Marktanalyse.

## Strategische Leitidee

> Nicht: Daten + Fotos.
> Sondern: Fotos erzeugen Daten.

## Produktkern (skizziert)

- **Onboarding**: Objektart, qm, Räume; optional Raumhöhen
- **Raumbuch** als Kernstück: Räume mit qm, Nutzung, Bodenbelag, frei erweiterbaren Feldern
- **Foto-Modul** als zentraler Erfassungspfad
- später: Ausstattung, Möbel, Geräte, Kosten, Schäden, Vorher/Nachher

## Foto-First Flow

1. Foto-Button als globaler CTA
2. Foto im Kontext aufnehmen (Raum/Objekt vorbelegt)
3. AI analysiert: Raumtyp, Objekt, Kategorie, Zustand, Marke, Preisbereich
4. Smart Confirmation Screen: User bestätigt in 3–5 Klicks
5. System erstellt/verknüpft: Immobilie ↔ Raum ↔ Objekt ↔ Foto ↔ Kategorie ↔ Metadaten

## Datenmodell-These

Foto als **Beziehungs-Knoten**: Foto ↔ Immobilie, Raum, Objekt(e), Kategorie, Zustand, Zeitpunkt.

## Verhältnis zu Immolizer

ImmoSkill ist **nicht** dasselbe wie [[immolizer]]: andere Kernfunktion (Dokumentation/Inventar vs. Bewertung/Vergleich), andere Erfassungslogik (Foto-First vs. Felder), anderes Job-to-be-done. Strategische Frage offen: eigenes Produkt, Modul oder Sub-Marke.

## Nächste Schritte

Offene Fragen zu Produkt-Positionierung, MVP-Scope, AI-Scope, Datenmodell und Monetarisierung in [[questions]] gesammelt.

## Quellen

- [[immoskill-brainstorming]]

## Verwandte Seiten

- [[questions]]
- [[immolizer]]
