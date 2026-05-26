# Coin Charts

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142333.png" alt=""><figcaption></figcaption></figure>

Charts for the majors + select memes. Open with key **7** or the MARKET WATCH home icon.

## List-First Layout

The screen opens as a clean list of all tracked assets — no big chart card up top. Each asset row shows its logo, ticker, name, current price, and 24h % change at a glance.

**Tap any row to expand it inline.** The expanded panel shows:
- 1D / 1W / 1M / 1Y timeframe tabs
- Big current price
- Sparkline chart for the selected timeframe
- HIGH / LOW / VOL / CHANGE stat grid

**Tap the row again to collapse it.** Only one asset is expanded at a time — tapping another auto-collapses the previous. The chevron rotates (▸ → ▾) to indicate state.

This replaces the older "fixed chart card at top, asset list below" design — saves vertical space and matches the RADAR layout pattern for consistency.

## D-Pad Navigation

- **Up/Down** → scroll the list
- **Left/Right** → cycle the timeframe (only when a card is expanded)
- **OK** → advance through assets (collapsed → BTC → ETH → ... → cycles back to collapsed)

## Coins Tracked

| Coin     | Source                                    |
| -------- | ----------------------------------------- |
| **SOL**  | Multiple                                  |
| **BTC**  | Multiple                                  |
| **ETH**  | Multiple                                  |
| **XRP**  | Bybit kline API                           |
| **HYPE** | Bybit kline API                           |
| **ZEC**  | Binance kline API (Bybit has no ZEC spot) |

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142410.png" alt=""><figcaption></figcaption></figure>

## Timeframes

1D / 1W / 1M / 1Y — per-card tabs inside each expanded panel.

Each chart is OHLCV (open/high/low/close/volume).

## Data Cache

Charts are fetched per-load with a short edge cache. We don't subscribe to streaming feeds during beta — this is a "lookup tool," not a "trading terminal." Background poll keeps each row's live price + 24h % fresh every 60s, so the collapsed list never goes stale.

## What It Is + Isn't

✅ A quick price + chart reference inside the phone ✅ Useful for verifying claims (was SOL really at $X yesterday?) ❌ Not a charting platform — no drawing tools, no indicators, no order entry ❌ Not connected to a brokerage

For deep TA, use TradingView or a proper terminal. For memecoin charts not listed here, use DexScreener directly. For perp signals + funding/whale data, use the **RADAR** app.
