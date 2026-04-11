---
title: "Prediction Markets"
type: concept
status: active
created: 2026-04-10
updated: 2026-04-10
tags: [prediction-market, trading, polymarket, market-microstructure]
confidence: medium
---

# Prediction Markets

## Definition

Prediction Markets sind Handelsplätze, an denen **Outcome-Shares** auf zukünftige Ereignisse gehandelt werden. Jede Share zahlt am Resolution-Zeitpunkt **$1** für das eingetretene Ergebnis und **$0** für alle anderen. Der laufende Marktpreis (typischerweise zwischen $0 und $1) entsteht durch Angebot und Nachfrage in einem Orderbook und wird als **implizierte Wahrscheinlichkeit** des Ereignisses gelesen.

## Abgrenzung zu Sportwetten / Buchmachern

| Dimension | Buchmacher | Prediction Market |
|---|---|---|
| Preisbildung | Anbieter setzt Quoten | Orderbook (Angebot/Nachfrage) |
| Gegenpartei | Anbieter selbst | andere User |
| Ausstieg vor Event | nur „Cashout" zu Hauskonditionen | echtes Trading (Sekundärmarkt) |
| Liquiditätsrisiko | gering (Quote garantiert) | Spread + Slippage |
| Anbieter-Marge | im Quote eingepreist | Trading-Fees / Spreads |
| Regulierung | Glücksspiel-Lizenz | Finanzregulierung / Event Contracts (jurisdiktionsabhängig) |

## Beispielrechnung

- „YES"-Share bei **$0,63** ⇒ Markt impliziert ~63 % Wahrscheinlichkeit
- Buchmacher-Quote **1,58** ⇒ ~63 % implizit, plus Buchmacher-Marge
- Bei Eintritt zahlt YES-Share $1, Profit pro Share = $0,37; bei Nicht-Eintritt = -$0,63

## Edge-Quellen (Trader-Perspektive)

1. **Bessere Information** — schwer, da Märkte schnell einpreisen
2. **Marktmikrostruktur** — Spread-Farming, Panik-Käufer/Verkäufer abkassieren („Hai im Orderbook")
3. **Arbitrage** — zwischen Märkten oder gegen externe Datenquellen
4. **Resolution-Risiko-Wissen** — Detailregeln und Edge-Cases der Resolution

Die zweite Kategorie dominiert öffentlich beobachtbare Wallets mit hohen Profit-Zahlen — Wins kommen nicht aus „besser vorhersagen", sondern aus diszipliniertem Algo-Trading.

## Beispielplattformen

- **Polymarket** — On-chain (USDC auf Polygon), CLOB-Architektur, größte Liquidität
- **Kalshi** — US-reguliert, CFTC-zugelassene Event Contracts
- **Augur**, **Manifold** — kleinere bzw. play-money-Varianten

## Implikationen

- Der angezeigte Preis ist **nicht** dasselbe wie eine kalibrierte Wahrscheinlichkeit — er reflektiert auch Liquidität, Risikoaversion und Marktteilnehmer-Bias
- Für Privatnutzer ohne Edge gilt: Limit Orders, Positionsgrößen disziplinieren, kein Market-Sell in Panik
- Für Engine-Bauer ist Risk Management und Reconciliation der schwierige Teil, nicht die Strategie

## Confidence

Mittel. Konzeptuelle Eckdaten gut belegt; einzelne Plattform-Details (Regulierung, Verfügbarkeit) ändern sich schnell — Stand April 2026.

## Relevante Quellen

- [[polymarket-vs-wettanbieter]]

## Verwandte Themen

- [[polymarket-trading-engine]]
