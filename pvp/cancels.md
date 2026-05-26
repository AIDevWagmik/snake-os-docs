# Cancels, Refunds & Retry

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141301.png" alt=""><figcaption></figcaption></figure>

## When a Match Can Be Cancelled

| State     | Can be cancelled? | By whom                               |
| --------- | ----------------- | ------------------------------------- |
| `waiting` | ✅ Yes             | Creator manually, or auto after 5 min |
| `ready`   | ✅ Yes             | Either player manually                |
| `playing` | ❌ No              | Match is in progress                  |
| `settled` | ❌ No              | Outcome already final                 |

## Retry Deposit (After Rejected Wallet Prompt)

If you accidentally cancel the Phantom approval popup on your deposit (or wallet errors out), you now have a **RETRY DEPOSIT** option on the matched view instead of being forced to LEAVE.

### How it works

1. After a rejected wallet prompt, the matched screen shows `⚠ DEPOSIT REJECTED`
2. Below the error, a new card appears: **RETRY DEPOSIT**
3. Pick a wager from the picker (0.05 / 0.1 / 0.2 / 0.5 SOL)
4. Tap **RETRY DEPOSIT (X SOL)**
5. Wallet popup fires again — approve to fund

### Can I change my wager on retry?

Yes — pick a different amount from the wager buttons before retrying. The server endpoint (`/api/pvp/update-wager`) validates:
- You're a player in the match
- You haven't already deposited (sig is null)
- Match status is `waiting` (P1) or `ready` (P2)
- New wager is in valid range (0.05 – 0.5 SOL)

If you've already deposited successfully, you can NOT change wager — you'd need to LEAVE (gets your refund) and create/join again.

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
