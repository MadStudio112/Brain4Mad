---
title: "Polymarket vs Wettanbieter"
type: source
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [polymarket, prediction-market, trading, source, dialog]
confidence: medium
---

# Polymarket vs Wettanbieter

## Summary

ChatGPT-Dialog-Clipping zu drei zusammenhängenden Themen:

1. **Mechanik-Vergleich Buchmacher vs. Polymarket** — warum Prediction Markets technisch und rechtlich anders funktionieren als klassische Wettanbieter
2. **„Whale-Wallet"-Analyse** — wie professionelle Trader auf Polymarket Marktmikrostruktur und Panik-Verkäufe ausnutzen, statt „besser vorherzusagen"
3. **Architektur-Plan für eine autonome Polymarket-Trading-Engine** — Komponenten, Auth, Daten, Strategien, Risk Management, plus Bewertung der Repos `oxmoei/poly-sdk` und `oxmoei/polyseer`

Im Originaltext mit Inline-Quellen verlinkt (Polymarket Docs, Reuters, X-Threads, GitHub-Repos).

## Key points

### Mechanik-Vergleich
- Buchmacher = Anbieter setzt Quoten, ist Gegenpartei, kalkuliert Marge — klassische Glücksspiel-Lizenz
- Polymarket = handelbare Outcome-Shares ($0–$1) mit Orderbook-Preisbildung; angezeigter Preis ≈ implizierte Wahrscheinlichkeit (Midpoint)
- Polymarket erlaubt echtes Vor-Event-Trading (Sekundärmarkt), Buchmacher höchstens „Cashout"
- Liquiditätsrisiko: bei Polymarket bekommst du keine garantierte Quote, sondern Spread/Slippage
- Regulierung jurisdiktionsabhängig; CFTC-Bewegung in den USA 2025; Geoblocking je nach Land

### „Whale-Wallet" / „Hai im Orderbook"
- Strategie ≠ bessere Vorhersage, sondern Spread-Farming zwischen Panik-Preis (1c–3c) und mathematischer Quasi-Sicherheit
- Begünstigt durch USDC-on-Polygon (niedrige Kosten, schnelle Trades) und fehlenden Buchmacher-Gegenpart
- Praktisches Takeaway: keine Market-Sells in Panik, Limit Orders, klare These, Positionsgröße diszipliniert
- swisstony als beobachteter Profit-Wallet auf Polymarket Leaderboard (~3,6M)

### Trading-Engine-Plan (Architektur)
- Standard-Algo-Trading-Pattern: Data → Signal → Risk → Execution → Ops
- Komponenten: Market Data Service (WS + REST), Strategy Engine, Risk Manager, Order Manager, Portfolio/Accounting, Ops
- Auth: L1 Private Key + L2 API Keys (aus Wallet abgeleitet); dediziertes Hot Wallet mit Cap
- Empfohlener MVP: passive Market-Making-Light um Midpoint mit Inventory Caps
- Risk Management ist nicht optional: Max Exposure pro Markt/Kategorie, Daily Loss Limit, Stale-Data Guard, Volatility Guard, Kill Switch
- Regel: LLMs für Research/Signal — nicht für Execution
- Build-Plan: Hello Market Data → Paper Trading → Real Trading mit 1 Markt → Risk Hardening → Multi-Market

### Repo-Bewertung
- **`oxmoei/poly-sdk`** (Fork von cyl19970726/poly-sdk): brauchbarer Accelerator für CLOB Trading, Market Data, Arbitrage-Scanning, Logging/Safety. Inoffiziell, gegen offizielle CLOB-Clients (`@polymarket/clob-client`, `py-clob-client`) auditieren.
- **`oxmoei/polyseer`**: AI-Research-Tool (Multi-Agent + Bayesian Aggregation), nicht Trading-Engine. Nur als Signal-Layer verwendbar.
- **`Polymarket/agents`**: offizielles Framework-Repo, Risk/Execution bleibt eigene Verantwortung.

## Important themes

- Prediction Market vs. Sportwetten als zwei strukturell unterschiedliche Modelle (Börse vs. Buchmacher)
- Marktmikrostruktur als Edge-Quelle, nicht Vorhersage-Genie
- Algo-Trading-Disziplin: Risk und Reconciliation sind die schwierigen Teile, nicht die Strategie
- LLM-Rolle in Trading-Systemen: Research ja, Execution nein

## Technische Referenzen (im Original verlinkt)

- Polymarket CLOB API Docs (REST + WebSocket, Order-Lifecycle, Authentication)
- `@polymarket/clob-client` (TypeScript), `py-clob-client` (Python), `rs-clob-client` (Rust)
- `oxmoei/poly-sdk`, `oxmoei/polyseer`, `Polymarket/agents`
- Reuters zu CFTC + Polymarket US-Rückkehr 2025

## Open questions

- Welche Sprache für eigene Engine: TypeScript (Stack-konsistent) oder Python (MVP-freundlich)?
- Reale Edge-Quelle: passt Market-Making-Light für ein kleines Budget oder werden Profis die Margen aufzehren?
- Rechtliche Lage in AT/EU für aktiven Polymarket-Handel als Privatperson
- Wie granular muss Backtest-Setup auf prices-history sein, um Execution-Logik realistisch zu validieren?

## Risks / caveats

- Quelle ist Dialog-Clipping (ChatGPT), keine geprüfte Primärquelle — die verlinkten Docs sind autoritativ, die Strategie-Aussagen sind Diskussionsstand
- Erwartung „autonome Engine = sicherer" ist falsch; Automatisierung beschleunigt nur Fehler
- `poly-sdk` und `polyseer` sind Community-Repos mit Audit-Bedarf

## File reference

- `raw/articles/polymarket-vs-wettanbieter.md`
