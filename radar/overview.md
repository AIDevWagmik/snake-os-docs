# What RADAR Does

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 145203.png" alt=""><figcaption></figcaption></figure>

RADAR is Snake OS's live perp-signal aggregator across **Hyperliquid** and **Phoenix**. It pulls real-time funding rates, predicted funding, open interest, whale taker fills, and tracked-wallet positions — surfacing the data points perp traders actually act on.

Open with the RADAR icon on the home screen.

## Who It's For

* Anyone deciding which perp to take
* Anyone watching for funding-flip / arb setups across venues
* Anyone tracking specific whale wallets' open positions

RADAR is read-only. It does not place trades — every venue is external, opened via the tap-to-leave links inside the app.

## Live for All Wallets

RADAR is available to every connected wallet. Earlier in beta it was dev-only while the data pipelines stabilized; now everyone has full access. The POSITIONS roster falls back gracefully for anonymous callers (active master seed only, no per-user customizations).

## Five Tabs

| Tab           | What it shows                                                                                                                                                |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **SPLITS**    | Cross-venue funding deltas (HYPER vs PHX), price spreads, predicted next funding, OI surges. Best for arb / funding-flip plays.                              |
| **HYPER**     | Top 20 Hyperliquid markets by 24h volume, full per-row stack.                                                                                                |
| **PHX**       | All active Phoenix markets.                                                                                                                                  |
| **WHALES**    | Real-time WebSocket stream of taker fills ≥ $50k across 12 watched coins. Tracked wallets show their named tags (e.g. "JamesWynn") instead of raw addresses. |
| **POSITIONS** | Open long/short books for a curated roster of 35+ named whales. Per-position size, leverage, entry, uPnL, distance-to-liq.                                   |

Each is detailed on its own page. See:

* [SPLITS / HYPER / PHX Tabs](markets.md)
* [WHALES Feed](whales.md)
* [POSITIONS — Tracked Wallets](positions.md)

## Data Sources

* **Hyperliquid Info API** — REST polling for markets, predicted funding, clearinghouse state
* **Phoenix Trade API** — REST for market list + WS for live data
* **trustfi backend** — for whale wallet enrichment and historical context

Polling cadence is tuned to each endpoint's rate limits. Funding refreshes every \~60s; mark prices every 15s; whale fills via WebSocket as they happen.

## ORACLE Bridge

When RADAR is open, its current snapshot is bridged into ORACLE chat. If you ask ORACLE "what perp should I take," it reads the live RADAR data and gives a directional read grounded in actual numbers. RADAR has to be open and recently-polled — if the data is stale (>5min), ORACLE falls back to general market knowledge.

## Notifications

RADAR's home-screen icon shows a notification badge when notable events fire:

* New named whale position opens
* OI surge ≥ 8% within 60min on any tracked coin

The badge clears when you open RADAR. Counter is per-device (localStorage), not server-synced.

## Disclaimer

> ⚠ RADAR is informational only. Any trades happen on the external venues (Hyperliquid, Phoenix). Snake OS does NOT custody perp positions, NOT process trades, NOT provide trading signals as financial advice. Use at your own risk. Funding rates and whale activity are public on-chain data — interpretation is yours.
