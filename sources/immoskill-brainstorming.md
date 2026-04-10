---
title: "ImmoSkill Brainstorming"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [immoskill, immolizer, proptech, photo-first, ai, source, brainstorming]
confidence: medium
---

# ImmoSkill Brainstorming

## Summary

Strukturiertes Brainstorming für ein Foto-zentriertes Immobilien-Erfassungs- und Inventarsystem unter dem Arbeitstitel **ImmoSkill**. Kernverschiebung gegenüber klassischen PropTech-Tools: Fotos sind nicht Dokumentation, sondern **Einstiegspunkt für Datenerfassung** — AI analysiert das Bild, schlägt Raum, Objekt, Kategorie und ggf. Marke/Preis vor, der User bestätigt mit minimalem Aufwand. Ergebnis ist ein hybrides „digitales Inventarsystem + digitale Immobilienakte". Das Dokument ist ein Dialog-Brainstorming, das in einer Markdown-Vorlage mit Checklisten endet, um eine zweite Brainstorming-Runde vorzubereiten.

## Key points

- Onboarding mit Objektart (Haus / Wohnung / Grundstück), Basisdaten (qm, Räume), optional Raumhöhen
- Kernstruktur: **Overview/Dashboard**, **Raumbuch** (Räume mit qm, Nutzung, Bodenbelag, erweiterbaren Feldern), Foto-Modul, später Ausstattung/Möbel/Geräte/Schäden
- **Strategische Leitidee**: „Nicht Daten + Fotos, sondern Fotos erzeugen Daten"
- Foto-Flow: Foto im Kontext aufnehmen → AI-Analyse → Smart Confirmation Screen mit Vorschlägen → strukturierte Speicherung und Verknüpfung
- Zwei UX-Modi: Quick Mode (1–2 Klicks, AI-bestätigend) und Detail Mode (Preis, Garantie, Seriennummer, Notizen)
- Killer-Idee: Räume entstehen automatisch, wenn mehrere Fotos auf einen Raumtyp deuten („Bett + Schrank + Fenster → Schlafzimmer?")
- Ein Foto wird als Beziehungs-Knoten gedacht (Immobilie ↔ Raum ↔ Objekt ↔ Kategorie ↔ Zustand ↔ Zeit), nicht nur als Tag-Träger
- Roadmap-Ausblick: Marktpreis-Erkennung, Schadenserkennung, Wartungsempfehlungen, Versicherungsreports, „Was fehlt im Raum?"-Analyse
- Endet mit einer kompletten `Brainstorming.md`-Vorlage in Markdown-Checklistenform als Grundlage für Runde 2 (MVP, UX-Flow, Datenmodell, AI-Scope, User Journey)

## Important themes

- **Foto-First-Onboarding** als UX-Differenzierer gegenüber formularbasierten PropTech-Tools
- AI als Beschleuniger und Assistenz, **nie als verpflichtender Schritt**
- Visuelles Inventarsystem mit Use Cases: Versicherung, Werttracking, Reparaturen, Vorher/Nachher-Vergleich
- Beziehungsmodell statt Tag-System — Fotos als zentraler Anker für Räume und Objekte
- Klare Trennung zwischen Quick und Detail Mode, um Power-User zu bedienen ohne Einsteiger zu überfordern

## Beziehung zu bestehenden Projekten

- **ImmoSkill ≠ [[immolizer]]**: Immolizer ist ein standardisierter, datenbasierter Bewertungs- und Vergleichs-Check (Typenschein, Benchmarks, Report). ImmoSkill ist eine visuelle, fotozentrierte Immobilien- und Inventarakte. Beide adressieren denselben Eigentümer, aber andere Jobs-to-be-done.
- Mögliche Konvergenz: ImmoSkills Raumbuch + Foto-Inventar könnte Immolizer als Datengrundlage füttern (Bewertung, Zustand, Ausstattungsqualität)
- Spannungsfeld: Noch keine Entscheidung, ob ImmoSkill eigenes Produkt, Modul von Immolizer oder neue Marke wird

## Open questions

- Ist ImmoSkill ein **eigenständiges Produkt**, ein **Modul von Immolizer** oder eine **Sub-Marke** unter einer Dachmarke?
- Welche AI-Erkennungen sind MVP-relevant und welche „Nice to Have"?
- Wie wird mit AI-Confidence und Fehlerkennungen umgegangen (Schwelle, Korrektur-UX)?
- Datenmodell: Wie sauber kann ein Foto gleichzeitig Raum, Objekt und Zustand referenzieren, ohne in Mehrfachzuordnungs-Konflikte zu laufen?
- Ab wie vielen kontextuellen Fotos wird ein Raum automatisch vorgeschlagen?
- Monetarisierung und Zielgruppe (Eigentümer, Vermieter, Versicherungen, Verwalter) — im Brainstorming nicht behandelt

## Risks / caveats

- Brainstorming-Charakter: Ideen sind nicht priorisiert, kein MVP-Cut, keine Aufwandsschätzung
- AI-Erkennungsqualität (Möbel, Marken, Preise) wird optimistisch angenommen — reale Genauigkeit muss geprüft werden
- Naming „ImmoSkill" steht im Spannungsverhältnis zu „Immolizer" und „FlatRace" (vgl. [[immolizer]] Naming-Spannungen)
- Doppelung mit Versicherungs-Inventar-Apps (z. B. Hausrat-Apps der Versicherer) als Wettbewerbsthema noch nicht adressiert

## File reference

- `raw/notes/immoskill-brainstorming.md`
