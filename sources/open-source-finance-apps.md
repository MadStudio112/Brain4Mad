---
title: "Open-Source Personal-Finance-Apps (Research)"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [finance, open-source, ux-reference, immolizer]
confidence: medium
---

# Open-Source Personal-Finance-Apps

Quelle: `raw/articles/open-source-finance-apps.md`

## Zweck der Research

Suche nach Open-Source Personal-Finance- und Haushaltsbudget-Apps als **UX- und Daten-Referenz** für [[immolizer]]. Immolizer soll Onboarding, Widget-Layout und Vergleichsdarstellung ähnlich klar wie reife Finance-Apps lösen.

## Kandidaten (Auswahl)

| App | Lizenz | Fokus | Bezug Immolizer |
|---|---|---|---|
| **Actual Budget** | MIT | Envelope-Budgeting, Multi-Device-Sync | Klare Kategorien-UX, Vergleichslogik |
| **Spliit** | MIT | Gemeinsame Ausgaben | Einfaches, modernes UI |
| **Firefly III** | AGPL | Selbst-gehostete Finanz-Suite | Sehr reichhaltig, dashboardorientiert |
| **Waterfly III** | — | Firefly-Client | Mobile-UX-Ideen |
| **Ivy Wallet** | — | Android, Kotlin | Visuelle Widget-Logik |
| **Cashew** | — | Cross-platform | Junge, freundliche UX |

## Lizenzfilter

Für potenzielle Code-Übernahme in das kommerziell gedachte Immolizer-Produkt sind **MIT/BSD/Apache** kompatibel, **AGPL** (Firefly III) nur als Referenz, nicht als Forking-Basis.

## Lern-Dimensionen

- **Onboarding**: Wie schnell kommt der User vom leeren Zustand zum ersten sinnvollen Wert?
- **Widget-Layout**: Welche Kennzahlen werden prominent gemacht, welche gruppiert?
- **Vergleichsdarstellung**: Absolute Zahl + relativer Kontext (Durchschnitt, Vorperiode)
- **Datenmodell**: Transaktion vs. Budget vs. Kategorie als Analogie zu Objekt/Widget/Feld bei Immolizer

## Einordnung

Diese Research ist **UX-Referenz**, kein eigenes Produkt. Relevanz fließt in [[immolizer]] als Designinspiration für das Dashboard-Pattern ein.
