---
title: "ImmoScout24 Datenintegration (Dialog-Clipping)"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [immolizer, immoscout24, api, datenintegration, oauth]
confidence: high
---

# ImmoScout24 Datenintegration

Quelle: `raw/articles/immoscout-datenintegration.md` (ChatGPT-Dialog)

## Zentrale Unterscheidung

1. **Import/Export API** — eigene Inserate anlegen/ändern/löschen (OAuth 1.0a, Business Account, kostenpflichtig, 2000 req/min). Standardweg für Makler-Workflows.
2. **Search API** — nur für Content-Partner, **nicht** als allgemeiner Datenfeed. Ohne explizite Freigabe darf der Portal-Datenbestand nicht als Marktdatenquelle verwendet werden.

Viele Startup-Ideen scheitern an dieser Unterscheidung — Immolizer muss den legalen Pfad explizit wählen.

## Architektur-Empfehlung

- **Adapter-Layer** `providers/immoscout/*` kapselt API-Spezifika
- **Staging-Tabelle** `source_payload_raw` speichert unveränderte JSON-Payloads (Audit + Reprocessing)
- **Transformer** (versioniert) wandelt Raw → Canonical Listing Schema
- **Domain Layer** von Immolizer/Flatrace arbeitet nur auf dem Canonical Schema, nie direkt auf ImmoScout-Feldern

## Canonical Listing Schema (Skizze)

`listing`, `listing_address`, `listing_notes`, `listing_pricing_rent`, `listing_building`, `listing_energy`, `listing_features`, `listing_contact_ref`, `listing_media_ref`, `listing_publication`, `source_raw`.

## Wichtige Fallstricke

- **Contact / Attachments / Publishing** sind eigene Endpoints, nicht im Real-Estate-Objekt enthalten
- **Date-Felder** dürfen keine GMT-Parameter tragen, sonst wird das Feld still ignoriert
- **Upsert** über `externalId` (URL-encoding bei `/`)
- **Rate-Limit-Handling** (429, Backoff) muss von Anfang an eingebaut werden
- **Compliance**: Speicher-Dauer, Weiterverarbeitung und Partnerstatus klären

## Mapping-Beispiel (apartmentRent → canonical)

Das Dokument enthält ein vollständiges Feld-für-Feld-Mapping für „Wohnung Miete":
`externalId → source_external_id`, `baseRent/totalRent/serviceCharge → listing_pricing_rent.*`, `livingSpace → area_living_m2`, `apartmentType/condition/interiorQuality → listing_building.*`, `heatingType/thermalCharacteristic → listing_energy.*`, usw.

## Relevanz

Dies ist die bislang detaillierteste technische Quelle zur Datenintegration für [[immolizer]]. Sie liefert (a) die Legitimitätsfrage (nur eigene Inserate ohne Partner-Status), (b) die Schichten-Architektur und (c) das initiale Mapping auf ein Canonical Schema.
