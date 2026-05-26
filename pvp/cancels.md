# Cancels & Refunds

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141301.png" alt=""><figcaption></figcaption></figure>

## When a Match Can Be Cancelled

| State     | Can be cancelled? | By whom                                       |
| --------- | ----------------- | --------------------------------------------- |
| `waiting` | ✅ Yes             | Creator manually, or auto after 5 min         |
| `ready`   | ✅ Yes             | Either player manually (admin tool currently) |
| `playing` | ❌ No              | Match is in progress                          |
| `settled` | ❌ No              | Outcome already final                         |

## How Cancels Work

When a cancel triggers:

1. Server CAS-flips `status: 'waiting' → 'cancelled'` (or `ready → cancelled`)
2. The CAS guard ensures only ONE cancel can succeed — no double-refund possible
3. For each side that deposited: server calls `sendPayout()` to send the wager back on-chain
4. Notification dropped to each refunded player with the refund TX signature

## What If a Refund Fails?

Rare but possible (RPC blip, treasury balance momentarily low). When `sendPayout` fails:

* The match stays `cancelled` (state already flipped)
* A `[pvp/lobby sweep] REFUND FAILED` entry is logged with the wallet + amount + match\_id
* The refund needs **manual reconciliation** by ops — report it in the support topic on Telegram with your wallet address
* We **never double-pay** — the CAS guard + deposit-sig uniqueness make that structurally impossible

## Auto-Cancel for Stuck Matches

Currently:

* ✅ **`waiting` matches** (nobody joined) → auto-cancel + refund after 5 min via the lobby sweep
* ❌ **`ready` matches** (both deposited but never started) → NOT auto-cancelled yet. Manual cleanup via admin. If you're stuck in a `ready` match and the opponent ghosts, please report it in the support topic on Telegram with the match ID.

Post-beta this will be cron-automated.
