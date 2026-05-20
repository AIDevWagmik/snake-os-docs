# Refund Didn't Arrive

## How long should I wait?

* Auto-refunds (lobby sweep, 5-min idle) typically arrive within **30 seconds of the cancel triggering**
* Manual cancel refunds typically arrive within **15 seconds**
* Solana network congestion can extend this to 1-2 minutes worst case

## Steps to debug

1. Check your wallet's transaction history for an incoming SOL TX from the treasury wallet
2. Check your notification panel in Snake OS — refunds drop a notification with the TX signature
3. Check Solscan for the treasury wallet's recent outgoing TXs

## If 5+ minutes pass and no refund

This is rare but possible (RPC blip, treasury balance momentarily low). The match is already `cancelled`, but the `sendPayout` call failed.

**Action:** post in our [Telegram support topic](https://t.me/snakeOS_sol) with:

* Your wallet address
* The match ID (visible in the PVP app history)
* The wager amount
* A screenshot of the cancellation notification if you got one

We can verify on-chain that the refund didn't process and send it manually. **We never double-pay** — the CAS guard + deposit-sig uniqueness make that structurally impossible. So if we send a manual refund, it's only ever the one that didn't go through.

## "I think I was charged twice"

You weren't, structurally. But if your wallet history is confusing:

1. Find the original deposit TX (you → treasury)
2. Find the refund TX (treasury → you) if it processed
3. Net = 0 if refund processed, or your deposit amount still out if it didn't

Report both TX hashes in our Telegram support topic if anything looks off.
