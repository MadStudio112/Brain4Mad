---
title: "EU Real Estate Platform Landscape"
type: topic
status: active
created: 2026-04-09
updated: 2026-04-09
tags: [proptech, real-estate, eu, platforms, market-landscape, immolizer]
confidence: medium
---

# EU Real Estate Platform Landscape

## Überblick

Der europäische Wohnimmobilien-Portalmarkt ist stark fragmentiert entlang nationaler Grenzen, aber strukturell konsolidiert durch wenige pan-europäische Konzerne. Jedes Land hat typischerweise 1–3 dominante Portale, oft gebunden an lokale Maklerverbände oder klassischen Medienkonzerne.

Detaillierte Länder-Tabellen: → [[eu-real-estate-platforms-western]] | [[eu-real-estate-platforms-southern]] | [[eu-real-estate-platforms-northern]] | [[eu-real-estate-platforms-eastern]]

---

## Strukturelle Muster

### 1. Maklerverband-Eigentum (NVM/Hemnet-Modell)
- Portale im Eigentum der nationalen Maklerverbände sichern sich durch Lock-in der Angebote Monopolstellung
- Beispiele: Funda.nl (NVM, NL), Hemnet (SE, Nasdaq-IPO 2021), Boligsiden (DK)
- Resultat: Sehr hohe Marktanteile, kaum Wettbewerb möglich
- Preismodell: B2B-Subscription oder Per-Listing für Makler; Suche für Nutzer kostenlos

### 2. Portal-First (Scout24-Modell)
- Unabhängige oder börsennotierte Portale mit starker Eigenmarke
- Beispiele: ImmoScout24 (DE/AT), Idealista (ES/IT/PT), Immobiliare.it (IT)
- Monetarisierung: Premium-Subscription für Makler/Inserenten + Werbung + Data-Services

### 3. Classifieds-Embedded (OLX / Schibsted-Modell)
- Immobilien als starke Kategorie in allgemeinen Kleinanzeigen-Plattformen
- Beispiele: LeBonCoin (FR), Kleinanzeigen (DE), Njuškalo (HR), SS.lv (LV)
- Vorteil: Hohe Gesamtreichweite; Nachteil: RE ist nicht Kernprodukt
- Freemium-Modell typisch

### 4. Privat-zu-Privat (PAP-Modell)
- Plattformen, die explizit Makler ausschließen
- Beispiele: PAP.fr (FR), Bezrealitky (CZ)
- Differenzierung über niedrige Kosten für Verkäufer, kein Maklergebühr-Signal

---

## Pan-Europäische Hauptakteure

| Konzern | Herkunft | EU-Portale | Anmerkung |
|---|---|---|---|
| **Aviv Group** | Axel Springer (Berlin) | SeLoger, Immoweb, Logic-Immo, Casa.it | Axel Springers RE-Tochter; hält mehrere nationale #1-Portale |
| **Scout24 SE** | Deutschland (DAX) | ImmoScout24 DE + AT | Fokus auf DACH; gut kapitalisiert |
| **Idealista Group** | Spanien (EQT-backed) | Idealista ES, IT, PT | Südeuropäische Expansion; IPO-Kandidat |
| **OLX Group** | Prosus/Naspers (NL/ZA) | Otodom (PL), Imovirtual (PT), Spitogatos (GR/CY) | RE-Portale über globales Classifieds-Netz |
| **Schibsted** | Norwegen (Oslo) | LeBonCoin (FR), Blocket (SE), Njuškalo (HR), XE.gr (GR) | Classifieds-Strategie |
| **Adevinta** | Schibsted-Spin-off (Permira 2023) | Kleinanzeigen (DE), Fotocasa (ES) | Nach Permira-Deal privatisiert |
| **Alma Media** | Finnland | Etuovi (FI), KV.ee (EE), City24 (EE/LV) | Nordisch + baltische Expansion |

---

## Marktgröße-Proxies (Europa gesamt, Schätzwerte)

> ⚠️ Alle Zahlen sind LLM-Schätzungen ~2024, keine verifizierten Statistiken.

- Gesamter EU Immobilientransaktionsmarkt: ~1.000-1.500 Mrd. € Volumen/Jahr (inkl. alle Transaktionen)
- Portal-Werbeumsätze EU gesamt: grob €1-2 Mrd./Jahr (sehr unsicher)
- Deutschland als größter Einzelmarkt: ImmoScout24 Revenue ~€600-700M (2023, unsicher)
- Hemnet (SE): ca. 700 Mio. SEK Revenue (2023), ca. 3,2 Mio. unique monthly visitors

---

## Besondere Muster je Region

### DACH
- Deutschland: Dreikampf Scout24 / Immowelt / Kleinanzeigen; Scout24 klar führend
- Österreich: Willhaben dominiert als Generalkleinanzeigen mit starker Immo-Kategorie
- Schweiz (nicht EU): Homegate + ImmoScout24.ch (außerhalb EU, aber hier als Referenz relevant)

### Westeuropa
- FR: LeBonCoin als Massenplattform, aber SeLoger für professionelle Suche stärker
- NL: Funda-Quasi-Monopol durch NVM-Kontrollstruktur; stärkster Lock-in in Europa
- BE: Immoweb klar führend dank früher Marktposition

### Nordeuropa
- SE: Hemnet-Dominanz ähnlich wie Funda in NL; IPO 2021
- FI: Duopol Alma (Etuovi) vs. Sanoma (Oikotie)
- DK: Boligsiden durch Maklerverband kontrolliert

### Südeuropa
- ES/IT/PT: Idealista stark, direkte Konkurrenz durch Aviv Group (Casa.it, Meilleurs Agents)
- GR/CY: OLX Group über Spitogatos
- MT: kein neutrales Portal; Agenturen dominieren

### Osteuropa
- PL: Otodom (OLX Group) klar führend
- CZ: Sreality (Seznam.cz) + disruptives Bezrealitky (privat-zu-privat)
- RO/BG/HR: Classifieds-Plattformen oft stärker als RE-Pure-Plays
- Baltics (EE/LV/LT): Alma Media (KV.ee, City24) + lokale Classifieds

---

## Relevanz für Immolizer

[[immolizer]] als Immobilien-Check-Tool (Typenschein, Bewertung, Betriebskosten) steht nicht in direktem Wettbewerb mit diesen Portalen, aber:

1. **Datenzugang:** Portale wie ImmoScout24, Funda, Hemnet haben proprietäre Marktdaten → Immolizer könnte auf öffentliche API-Daten, Scraped-Daten oder Partnership-Daten angewiesen sein
2. **Vertriebskanal:** RE-Portale könnten Partner sein (Einbettung des Immolizer-Checks in Listings)
3. **Wettbewerb indirekt:** Portale bauen eigene Bewertungstools (ImmoScout24 Bewertung, Idealista-Valuations) → potenziell sich überlappende Features
4. **DACH-Fokus:** Für AT/DE-Startphase: Willhaben.at + ImmoScout24.at + ImmoScout24.de sind die relevantesten Plattform-Umfelder

## Verweise

- [[eu-real-estate-platforms-western]]
- [[eu-real-estate-platforms-southern]]
- [[eu-real-estate-platforms-northern]]
- [[eu-real-estate-platforms-eastern]]
- [[immolizer]]
- [[eu-real-estate-platforms-research]] (Quellen-Note)
