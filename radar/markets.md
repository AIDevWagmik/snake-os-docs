# SPLITS · HYPER · PHX Tabs

These three tabs show the market-level data for tracked perps. Each row is one coin (asset), with a logo + ticker, and can be expanded to reveal venue-specific stats.

## SPLITS Tab

The cross-venue comparison view. Shows HYPER vs PHX side-by-side for each pinned asset (BTC, ETH, SOL plus auto-included top-N by volume).

**What you see per asset row:**

- Logo + ticker
- HYPER funding rate (%/hour) + PHX funding rate
- **Funding delta (Δ)** — HYPER minus PHX, per hour
- HYPER + PHX mark prices
- **Price spread %** — flagged when meaningful
- Open interest (HYPER)
- 24h volume (HYPER)
- **OI surge** — rolling 60-min change in open interest
- **Predicted next funding** — Hyperliquid's forward-looking rate + minutes to pay

**Why SPLITS matters:**

A wide funding delta (e.g. HYPER paying +0.02%/h while PHX paying -0.02%/h) means one venue is more crowded long than the other. That's an arb signal — short the over-paid side, long the under-paid side, capture the spread. Combined with a visible price spread between the two venues, you've got the setup.

## HYPER Tab

The full Hyperliquid market view. Top 20 markets by 24h volume.

Per-row:
- Funding %/h
- Predicted next funding + countdown
- Mark price
- 24h volume USD
- Open interest USD
- OI surge if active

Click an asset row to expand — reveals everything stacked vertically with the venue-jump button to open Hyperliquid for that pair.

## PHX Tab

Same shape as HYPER, but for Phoenix Trade markets. Fewer assets, slightly different liquidity profile, often different funding regimes from HYPER for the same coin.

## Reading Funding Rates

- **Positive funding** = longs pay shorts → market is crowded long → often a fade signal at extremes
- **Negative funding** = shorts pay longs → crowded short → often a squeeze setup at extremes
- **Funding compounds hourly** — what looks small (+0.02%/h) is +0.48%/day for the wrong side
- **Predicted funding** in the "next X% in Ym" field is Hyperliquid's forward calc — use it to time positioning

## OI Surge Read

OI surge = rolling 60-minute change in open interest. The system flags surges ≥ 8%.

- **+OI surge with positive funding** → longs piling in, watch for blow-off
- **+OI surge with negative funding** → short squeeze fuel building
- **−OI surge** → de-risking, position unwind in progress

## Venue Jump

Each asset row has a venue badge (HYPER or PHX). Tapping it opens the live trading page on the venue itself (external link, you'll see the "Leaving Snake OS" confirmation modal first).

## Expand to See Detail

By default each row is collapsed — just logo, ticker, primary metric. Tap the row to expand the full per-venue stack. Tap again to collapse. Keeps the page short and scannable when there are 20+ markets in view.
