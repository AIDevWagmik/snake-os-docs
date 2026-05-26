# WHALES Feed

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 145353 (1).png" alt=""><figcaption></figcaption></figure>

Real-time stream of taker fills ≥ $50,000 across 12 watched coins on Hyperliquid. Updates as fills happen via WebSocket — no polling delay.

## What Each Fill Shows

* **Coin** (BTC, ETH, SOL, HYPE, etc.)
* **Side** (BUY / SELL)
* **USD notional** (e.g. $128,400)
* **Age** (e.g. 3m ago)
* **Taker** — wallet address. If it matches a wallet in our tracked roster, you see the **named tag** (e.g. "JamesWynn") instead of the raw address. Tap the address to open the Hyperliquid explorer for that wallet.

## Collapsible Per Coin

Fills group by coin. Each coin card shows:

* Coin ticker + total fills count
* Net flow direction (BUY-leaning, SELL-leaning, or balanced)
* Combined USD volume across all visible fills

Tap a coin to expand and see the individual fills sorted newest-first.

## Threshold + Watched Coins

* **Minimum fill size:** $50,000 USD notional
* **Watched coins:** 12 (BTC, ETH, SOL, HYPE, plus 8 rotating top-volume alts)
* **Retention:** Up to 60 fills kept in localStorage so a fresh RADAR open shows recent context, not an empty list

## How To Use This

* **Side imbalance** = directional pressure. "3 of the last 4 HYPE fills were buys" = bullish flow signal
* **Named whale fills** carry more weight than anonymous flow. A 200k buy from "JamesWynn" is conviction; the same from `Hd7p…fK9` is random
* **Cluster timing** matters. 4 buys within 5 minutes from different whales = coordinated FOMO; 4 buys over 4 hours = noise

## (MM) Tags

Wallets tagged `(MM)` in the roster are **market makers** — their flow is delta-neutral hedging, not directional conviction. Discount any directional read from their fills. Their activity tells you about market liquidity, not about price direction.

## Notifications

A new named-whale fill bumps the RADAR badge counter. So even with the app closed, you'll see a count on the home-screen RADAR icon when a tracked whale takes size.
