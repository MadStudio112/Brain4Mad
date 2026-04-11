---
title: "Open-Source Finance Apps als UX-Referenz"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [finance, open-source, ux-reference, immolizer]
confidence: medium
---

# Open-Source Finance Apps als UX-Referenz

## Zweck

Dieses Thema bündelt Open-Source Personal-Finance- und Haushaltsbudget-Apps, die als **UX- und Struktur-Referenz** für [[immolizer]] dienen. Ziel ist nicht die Finanzdomäne selbst, sondern die Übernahme reifer Design- und Datenmuster für Onboarding, Widgets und Vergleichsdarstellung.

## Kandidaten

- **Actual Budget** (MIT) — Envelope-Budgeting, sehr saubere Kategorien-UX
- **Spliit** (MIT) — leichte, moderne Oberfläche
- **Firefly III** (AGPL) — reichhaltige, dashboardorientierte Suite; AGPL → nur Referenz
- **Waterfly III** — Firefly-Client, Mobile-UX
- **Ivy Wallet** — Android/Kotlin, visuelle Widget-Logik
- **Cashew** — Cross-platform, junge freundliche UX

## Relevante Muster für Immolizer

1. **Onboarding**: Leerer Zustand → erster sinnvoller Wert in wenigen Schritten
2. **Widget-Layout**: Prominente Kennzahlen + gruppierte Sekundärdaten
3. **Vergleichsdarstellung**: Absolute Zahl + relativer Kontext (Durchschnitt / Vorperiode / Kategorie)
4. **Datenmodell-Analogie**: Transaktion ↔ Immobilien-Fakt · Budget ↔ Zielwert · Kategorie ↔ Feldgruppe

## Lizenzhinweis

Für potenzielle Code-Übernahme ins kommerziell gedachte Immolizer-Produkt sind **MIT / BSD / Apache 2.0** nutzbar, **AGPL** nur als konzeptionelle Referenz.

## Quellen

- [[open-source-finance-apps]]

## Verwandte Themen

- [[immolizer]]
