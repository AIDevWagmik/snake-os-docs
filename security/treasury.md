# Treasury Escrow

The treasury wallet holds escrow during PvP matches and processes refunds + payouts.

## Treasury Wallet Address

The full address is published in the app footer + Snake OS X bio. This is the wallet that:

* Receives PvP deposits
* Receives market purchases
* Sends PvP refunds (on cancel)
* Sends PvP payouts (on claim)

## Key Management

Currently during beta:

* Private key stored as a Wrangler secret (Cloudflare Worker)
* Never logged, never committed to source
* Only the Worker code can sign with it

Post-beta migration:

* Move to **KMS** (Cloudflare or AWS) for stronger key isolation
* Or multi-sig with 2-of-3 signers for higher trust assumption
* This migration is scoped for post-launch (current scale doesn't require it)

## Treasury Liquidity

* Beta target: **≥ 1.5 SOL hot** at all times
* Post-launch target: **≥ 5 SOL hot**, alert at 2 SOL
* Treasury runs an automated buy-back operation post-launch — see [Treasury & Buybacks](../snake-token/treasury.md)

## What If Treasury Runs Dry?

If treasury balance is temporarily insufficient for a payout:

* `sendPayout` fails with a clear error
* The user's `claimable_pvp_sol` balance is **restored** (atomic reserve pattern)
* User can retry the claim
* Ops monitors treasury balance and tops up as needed

Nothing is ever lost — the user's claimable balance is the source of truth.

## What If Treasury Wallet Is Compromised?

In the worst-case scenario:

* Treasury SOL could be drained
* BUT user assets (in their own wallets) are NOT at risk — we never have their keys
* Outstanding `claimable_pvp_sol` balances are still recorded — Snake OS would need to fund a new treasury and pay them
* This is a brand-existential event, not a user-funds event

Post-launch KMS migration is specifically to make this scenario nearly impossible.
