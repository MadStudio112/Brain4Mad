---
title: "JMail.world — technische Umsetzung (Dialog)"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [reference, architecture, nextjs, vercel, cloudflare, data-pipeline]
confidence: medium
---

# JMail.world — technische Umsetzung

Quelle: `raw/notes/jmail-umsetzung-dialog.md` (ChatGPT-Dialog)

## Kontext

jmail.world ist **kein eigenes Projekt**, sondern eine Referenz-Architektur, die als Vorlage für mögliche andere Content- und Such-Plattformen aus dem MadStudio-Portfolio dient.

## Stack

- **Frontend / App**: Next.js auf Vercel (SSR + ISR gemischt)
- **Edge**: Cloudflare (Caching, Routing, ggf. Workers)
- **Datenpipeline**: PDF → JSON → Index
  - Ingest der Roh-PDFs
  - Normalisierung in strukturiertes JSON
  - Indexierung für Such-/Filterzugriff
- **Hybride SSR-Strategie**: dynamische Seiten server-gerendered, Listen/Static über ISR

## Lern-Dimensionen für eigene Projekte

- **Dokumenten-Pipeline**: Muster für [[immolizer]] (Exposé-PDFs → strukturierte Felder) und ggf. [[teamchef]] (Match-Reports)
- **SSR-Mix**: Blueprint für SEO-relevante Portfolio-Seiten
- **Vercel + Cloudflare Kombination**: praktikabel bei strengen Latenz- und Cache-Anforderungen

## Einordnung

Reine Referenz. Gehört nicht in die Projektliste, sondern als **externe Architektur-Blaupause** ins Wiki.
