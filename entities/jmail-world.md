---
title: "jmail.world"
type: entity
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [reference, architecture, nextjs, vercel, cloudflare, data-pipeline]
confidence: medium
---

# jmail.world

## Kurz

Externe Plattform, die hier **rein als Architektur-Referenz** geführt wird. Kein eigenes MadStudio-Projekt.

## Stack

- **App**: Next.js auf Vercel, gemischtes SSR/ISR
- **Edge**: Cloudflare (Caching, Routing)
- **Datenpipeline**: PDF → JSON → Index

## Warum hier?

Das Muster „Dokumenten-Ingest → Normalisierung → Index" ist übertragbar auf:

- [[immolizer]] — Exposé-PDFs zu strukturierten Objektfeldern
- mögliche zukünftige Such-/Portfolio-Projekte

## Quellen

- [[jmail-umsetzung-dialog]]
