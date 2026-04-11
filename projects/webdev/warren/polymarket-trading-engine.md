---
title: "Polymarket Trading Engine"
type: topic
status: draft
created: 2026-04-10
updated: 2026-04-10
tags: [polymarket, trading, algo-trading, prediction-market, project-idea]
confidence: low
---

# Polymarket Trading Engine

## Summary

Konzeptskizze für eine **autonome Trading-Engine auf Polymarket**, die mit einem fest gecappten Budget eigenständig handelt. Standard-Algo-Trading-Architektur, kein „magischer KI-Trader". Status: Architekturplan und Repo-Bewertung, noch kein Code, kein MVP.

## Zielbild

- Engine handelt eigenständig auf Polymarket CLOB
- Hot Wallet mit hartem Cap als Risikobegrenzung
- Strategie regelbasiert, deterministisch und testbar
- LLM (falls überhaupt) nur für Research/Signal, **nicht** für Execution

## Architektur (Komponenten)

1. **Market Data Service** — WebSocket-Subscriptions (Orderbook, Trades) + REST-Fallback, lokaler Orderbook-Cache mit best bid/ask, Depth, Midpoint
2. **Strategy Engine** — generiert deterministische „Order Intents" (place/cancel/replace mit Preis, Size, Side)
3. **Risk Manager** — Budget-Allokation, Exposure-Limits, Loss-Limits, Kill Switch
4. **Order Manager (Execution)** — signiert und sendet Orders via CLOB API, Cancel/Replace, Idempotency, Rate-Limit-Handling, Reconciliation
5. **Portfolio / Accounting** — Positionen pro Token/Markt, realized/unrealized PnL, Fees, Cash
6. **Ops** — Structured Logging, Metrics, Alerts, Persistenz (z. B. Supabase/Postgres)

## Auth & Security

- Polymarket CLOB hat zwei Auth-Ebenen: **L1** (Private Key / Wallet) und **L2** (API Keys, aus Wallet abgeleitet)
- Dediziertes Hot Wallet ausschließlich fürs Bot-Trading mit hartem Cap
- Private Key niemals in Logs/DB; Secrets Manager oder Hardware
- L2 API Credentials für die meisten privaten Endpoints

## Strategien (Realismus-Reihenfolge)

### Strategie A: Passive Market-Making Light (MVP-Empfehlung)
- 2-seitige Quotes knapp innerhalb best bid / best ask
- Quote nur bei `spread >= X`
- Inventory Cap pro Markt (z. B. 2–5 % Budget)
- Cancel/Replace bei Midpoint-Drift oder Verlust der Top-of-Book-Position
- **Wert für die Engine**: zwingt zur sauberen Lösung von Orderbook, Partial Fills, Cancels, Reconcile — also genau die schwierigen Operations-Probleme

### Strategie B: Event-Driven / News
- Nur sinnvoll mit echtem Informationsvorsprung
- Sonst durch schnellere Bots unmittelbar zerlegt

### Strategie C: Cross-Market / Hedge
- Korrelationen oft fragil
- Resolution-Regeln und Edge-Cases können Hedge zunichtemachen

## Risk Management (nicht optional)

| Limit | Beispielwert |
|---|---|
| Max Exposure pro Markt | 3 % Budget |
| Max Exposure pro Kategorie | 10 % Budget |
| Max Order Size | 0,25 % Budget |
| Max Open Orders | 20 |
| Daily Loss Limit | -2 % → Bot stoppt |
| Stale Data Guard | WS hängt → alles canceln, pausieren |
| Volatility Guard | Spread explodiert / dünnes Buch → pausieren |

## Datenmodell (z. B. Supabase)

- `markets` (market_id, title, category, end_time, rules_hash)
- `tokens` (token_id, market_id, outcome)
- `order_intents` (ts, token_id, side, price, size, reason)
- `orders` (order_id, token_id, side, price, size, status)
- `fills` (trade_id, order_id, price, size, fee, ts)
- `positions` (token_id, net_shares, avg_price)
- `risk_state` (budget, exposure_by_market, pnl_today, kill_switch)

## Build-Plan (5 Stufen)

1. **Hello Market Data** — WS subscribe, Orderbook-Cache, Persistenz
2. **Paper Trading Mode** — gleiche Engine ohne echte Orders
3. **Real Trading mit 1 Markt** — winziges Budget, Market-Making Light
4. **Risk Hardening** — Kill Switch, Reconcile, Alerts
5. **Multi-Market + Strategy Iteration** — erst jetzt skalieren

## Repo-Landschaft (Stand 2026-04)

| Repo | Rolle | Empfehlung |
|---|---|---|
| `Polymarket/clob-client` (TS) | offizieller CLOB-Client | Referenz für Auth/Order-Placing |
| `Polymarket/py-clob-client` (Python) | offizieller Client | Referenz für Python-Stack |
| `Polymarket/rs-clob-client` (Rust) | offizieller Client | optional |
| `Polymarket/agents` | offizielles Agent-Framework | Risk/Execution bleibt eigene Verantwortung |
| `oxmoei/poly-sdk` (Fork) | Trading-/Infra-Accelerator (CLOB, Market Data, Arbitrage-Scanning, Logging, Safety Limits) | brauchbarer Beschleuniger, **gegen offizielle Clients auditieren** |
| `oxmoei/polyseer` | AI-Research-Tool (Multi-Agent + Bayesian) | nur Signal-Layer, **nicht** Execution |

## Was wir konkret brauchen

- Hot Wallet + Cap, Secrets Handling
- Stack-Entscheidung: TypeScript (Konsistenz mit restlichem Stack) oder Python (MVP-Geschwindigkeit)
- Execution Core: WS Orderbook Cache, place/cancel/replace, Reconcile-Loop, hart kodierte Risk Limits
- Persistenz (Supabase) für Orders, Fills, Positions, Risk State
- Paper Trading Mode bevor echtes Geld fließt
- Backtest-Setup auf `prices-history` und Trades
- Monitoring: Healthchecks, Auto-Restart, remote togglebarer Kill Switch

## Offene Fragen

- **Stack**: TypeScript oder Python für die erste Version?
- **Rechtslage**: Polymarket-Zugang für Privatpersonen in AT/EU; KYC und Steuerthemen
- **Edge**: ist Market-Making Light mit kleinem Budget profitabel oder werden Profis die Margen aufzehren?
- **Backtest-Realismus**: wie genau lässt sich Slippage und Fill-Wahrscheinlichkeit aus historischen Daten rekonstruieren?

## Confidence

Niedrig. Architekturplan ist solides Standard-Algo-Trading, aber konkrete Edge-Hypothese, rechtliche Voraussetzungen und Aufwand sind nicht validiert.

## Relevante Quellen

- [[polymarket-vs-wettanbieter]]

## Verwandte Konzepte

- [[prediction-markets]]
