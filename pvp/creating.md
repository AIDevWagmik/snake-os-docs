# Creating a Match

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141124.png" alt=""><figcaption></figcaption></figure>

## Step-by-Step

1. Open **PVP** app.
2. Tap **CREATE MATCH**.
3. Enter your wager amount in SOL (between 0.01 and 10).
4. Confirm — a `pvp_matches` row is created with status `waiting`.
5. Approve the on-chain deposit transaction in your wallet.
   * SOL goes to the treasury wallet (escrow)
   * The TX signature is recorded as `p1_deposit_sig`
6. Wait for an opponent. Your match shows in the lobby for everyone to see.

## Auto-Cancel Protection

If no opponent joins within **5 minutes**, the system auto-cancels your match and refunds your deposit on-chain. You'll get a notification:

> _"PvP match expired — wager refunded. Nobody joined within 5 minutes. Your X SOL wager has been refunded."_

The refund TX signature is included in the notification.

## Manual Cancel

You can cancel a `waiting` match yourself anytime:

1. Open your match in the lobby
2. Tap **CANCEL MATCH**
3. Confirm — status flips to `cancelled` (CAS-guarded), refund auto-fires on-chain

## What If I Create Then Disconnect?

The match stays in `waiting` for up to 5 minutes. If you reconnect within that window, you'll see your match in the lobby. If 5 minutes pass, it auto-cancels and refunds.

## What If I Create Two Matches?

You can't — creating a new match while you have an existing `waiting` match auto-cancels the old one first (and refunds the deposit), then creates the new one. This prevents duplicate lobbies clogging the list.
