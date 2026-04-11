---
title: "ImmoSkill"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-11
tags: [immoskill, immolizer, proptech, photo-first, ai, inventar, product]
confidence: low
---

# ImmoSkill

## Summary

ImmoSkill ist ein Konzept für eine **foto-zentrierte Immobilien- und Inventarakte**. Der zentrale Bruch zur klassischen PropTech-Logik: Fotos sind nicht Dokumentation, sondern **Einstiegspunkt für die Datenerfassung**. AI analysiert das Bild, schlägt Raum, Objekt, Kategorie und ggf. Marke/Preis vor, der User bestätigt mit minimalem Aufwand. Resultat ist ein hybrides „digitales Inventarsystem + digitale Immobilienakte".

Status: frühes Brainstorming, keine MVP-Definition, kein Datenmodell, keine Marktanalyse.

## Strategische Leitidee

> Nicht: Daten + Fotos.  
> Sondern: Fotos erzeugen Daten.

AI ist Beschleuniger, nie verpflichtend. User bleibt in Kontrolle, formularlastige Erfassung wird so weit wie möglich ersetzt.

## Produktkern (skizziert)

- **Onboarding**: Objektart (Haus / Wohnung / Grundstück), qm, Räume; optional Raumhöhen
- **Overview / Dashboard** mit Kennwerten der Immobilie
- **Raumbuch** als Kernstück: Räume mit qm, Nutzung, Bodenbelag, frei erweiterbaren Feldern
- **Foto-Modul** als zentraler Erfassungspfad
- später: Ausstattung, Möbel, Geräte, Kosten, Schäden, Vorher/Nachher

## Foto-First Flow

1. Foto-Button als globaler CTA (Dashboard, Raum, Objekt)
2. Foto wird im Kontext aufgenommen (Raum/Objekt vorbelegt)
3. AI analysiert: Raumtyp, Objekt, Kategorie, optional Zustand, Marke, Preisbereich
4. Smart Confirmation Screen: User bestätigt oder korrigiert in 3–5 Klicks
5. System erstellt/verknüpft automatisch Immobilie ↔ Raum ↔ Objekt ↔ Foto ↔ Kategorie ↔ Metadaten

### Zwei UX-Modi
- **Quick Mode** (Default): AI-Vorschläge, 1–2 Klicks, < 5 s
- **Detail Mode**: Preis, Garantie, Seriennummer, Notizen

### Killer-Idee „Raum entsteht durch Fotos"
Mehrere Fotos (z. B. Bett + Schrank + Fenster) → System schlägt Raum „Schlafzimmer" zur automatischen Anlage vor.

## Datenmodell-These

Foto ist kein Tag-Träger, sondern **Beziehungs-Knoten**:

- Foto ↔ Immobilie
- Foto ↔ Raum
- Foto ↔ Objekt(e)
- Foto ↔ Kategorie
- Foto ↔ Zustand
- Foto ↔ Zeitpunkt

Daraus entstehen Filter wie: alle Schadenfotos der Wohnung, alle Fotos eines Möbelstücks, Vorher/Nachher-Vergleich.

## Use Cases

- Versicherungs-Inventar (Hausrat-Wertnachweis)
- Werttracking von Möbeln und Geräten
- Schadens- und Reparaturdokumentation
- Übergabeprotokoll (Mieterwechsel, Verkauf)
- Wartungs- und Garantie-Tracking
- Roadmap: „Was fehlt im Raum?"-Analyse, Marktpreis-Vorschläge

## Verhältnis zu [[immolizer]]

ImmoSkill ist **nicht** dasselbe wie [[immolizer]]:

| Dimension | Immolizer | ImmoSkill |
|---|---|---|
| Kernartefakt | standardisierter A4-Check / Typenschein | visuelle Immobilienakte + Inventar |
| Erfassung | strukturierte Felder, Marktdaten | Fotos + AI-gestützte Strukturierung |
| Job-to-be-done | Bewertung, Vergleich, Entscheidung | Dokumentation, Inventar, Nachweis |
| Output | Report, Benchmarks | Akte, Galerie, Beziehungs-Graph |

Beide adressieren denselben Eigentümer und könnten konvergieren — ImmoSkills Raumbuch und Foto-Inventar könnten Immolizer als Datengrundlage füttern (Zustand, Ausstattungsqualität). Strategische Frage offen: eigenes Produkt, Modul von Immolizer oder Sub-Marke unter einer Dachmarke?

## Offene Fragen

Produkt-Positionierung, MVP-Scope, AI-Scope, Datenmodell, Monetarisierung und Zielgruppen-Abgrenzung — gesammelt in [[immoskill-open-questions]].

## Confidence

Niedrig. Reines Brainstorming, kein MVP-Cut, kein Datenmodell, keine Marktanalyse, keine Aufwandsschätzung.

## Relevante Quellen

- [[immoskill-brainstorming]]

## Verwandte Themen

- [[immolizer]]
