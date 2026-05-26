# POSITIONS — Tracked Wallets

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 145439.png" alt=""><figcaption></figcaption></figure>

The POSITIONS tab shows live open long/short books for a curated roster of 35+ named whale wallets. Per-position size, leverage, entry, uPnL, and distance-to-liquidation.

## What You See

Each wallet appears as a card:

* **Label** (e.g. "JamesWynn", "greg", "ABC", "pensionfund", "bobbybigsize")
* **MM tag** if the wallet is a market maker (delta-neutral, discount directional reads)
* **Net side tag** — NET LONG / NET SHORT / FLAT / IDLE (calculated from notional sum)
* **Open position count badge** — quick read of how many active positions
* **Hyperliquid explorer link** — tap the address to view their full account
* **Rename / Remove buttons** — customize your own view (per-wallet)

Tap the card header to expand and see the wallet's open positions:

* **Side** (▲ LONG / ▼ SHORT)
* **Coin + leverage** (e.g. HYPE 10x)
* **Notional USD**
* **Size + entry price** (e.g. 4,200 HYPE @ 24.10)
* **uPnL** (unrealized PnL in USD, colored)
* **Distance to liquidation** — % away from getting wicked. Colored:
  * Red < 3% (about to blow)
  * Orange < 10% (warning)
  * Yellow < 25% (notable)
  * Dim green ≥ 25% (safe)

## Aggregate Strip

At the top of POSITIONS, a one-line aggregate of the entire roster:

* **Active wallets** — of total
* **Total LONG notional** (USD)
* **Total SHORT notional** (USD)
* **Combined uPnL** across all positions

Quick read of the room's positioning.

## Hide-Idle Toggle

By default, wallets with zero open positions are hidden — they bloat the page without adding signal. A footer toggle lets you reveal them ("Show X idle wallets in cash") when you want to prune your roster or see who's flat.

## Custom Wallets (Connected Only)

The roster is **server-backed** (Supabase tables). Your customizations follow you across devices:

* **Add a wallet** to your personal roster (dev-only currently — see below)
* **Rename a wallet** for your view (server stores your alias, others see the default)
* **Remove a wallet** from your view (hides it just for you, doesn't affect anyone else)

These are per-user customizations. The base seed roster of 35+ wallets is admin-managed.

### Add Wallet — Dev Only

The "+ ADD WALLET" form at the bottom of the POSITIONS tab is currently restricted to the dev wallet. The reasoning: the curated master seed should remain the source of truth for everyone. Regular users still see the full roster + can rename or hide entries in their own view.

If you're a dev wallet, the form appears at the bottom of the list. Paste the wallet address + optional label, click ADD. Validates as 0x + 40 hex chars.

## Polling

The roster's positions refresh every 30 seconds via Hyperliquid's `clearinghouseState` endpoint. Each wallet is queried independently and batched gently to respect rate limits.

A footer shows when positions were last refreshed: _"Updated 14s ago · polls 30s"_.

## Distance-to-Liq Math

For each open position with a known liquidation price + current mark:

* **LONG:** distance = (mark − liq) / mark
* **SHORT:** distance = (liq − mark) / mark

Distance is asymmetric by side — longs get liquidated when price falls below liq, shorts when price rises above. The percentage tells you how much the underlying must move against the position before it's wicked.

## Migration 026

The roster + customizations are powered by `radar_seed_wallets` (master) + `user_whale_roster` (per-user). If you previously saw this feature backed by localStorage only, it's been migrated to server-side storage so your customizations sync across devices.
