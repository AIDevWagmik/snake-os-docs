# Who Earns Tokens

See [Reward Eligibility](../rewards/eligibility.md) for the complete policy.

## Three Paths to Earning

| Path | What you do | What you earn |
| ---- | ----------- | ------------- |
| **BITS** | Use any Snake OS app — game, trade, explore, chat | BITS → weekly token share from the burn pool |
| **PvP** | Win PvP matches | SOL winnings + weekly token prize distributions (top players) |
| **Hold** | Hold tokens in your wallet | Weekly holder buyback distributions (post-launch) |

## BITS — The Primary Earning Path

BITS are earned across all Snake OS apps with no minimum spend required. Every user starts earning from their first session. Your accumulated BITS determine your proportional share of the weekly burn pool after launch.

Stack BITS now during beta — they carry forward to launch.

## Holder Gate — Post-Launch Token Claims

Direct token reward claims (achievement-linked token rewards, if any) are only payable to wallets that already hold tokens in their connected wallet. Any non-zero balance qualifies.

**Why this gate exists:**

1. **Treasury saves rent.** Sending tokens to a wallet that has never held them requires creating an Associated Token Account (~0.002 SOL). Holders already have an ATA, so the transfer skips that cost.
2. **Filters farming accounts.** Wallets with no position have zero conviction. Buying first means anyone claiming has skin in the game.
3. **Reinforces the earn model.** BITS are the primary pre-launch path; the holder gate applies to secondary direct-token flows that open post-launch.

**Threshold:** Any non-zero balance qualifies. A small bag is enough.

**What you'll see without tokens:**

> "Token claims are for holders of the token only"

The claim is blocked with a 403. Buy any amount on Jupiter, then claim.

### Pre-launch

Until the token mint is deployed and activated on the production server, all direct token claims return a 503 "token claims not enabled yet." The BITS burn pool exchange is what opens at launch — not a separate claim gate.

## What Does NOT Earn Tokens

The following are intentionally excluded from the reward model:

* ❌ Logging in daily (no login streaks)
* ❌ Adding friends alone (cosmetic badge only)
* ❌ Just signing up (no sign-up drop)
* ❌ Referring others (no referral program)

These are the patterns that attract farmers. By routing rewards through BITS (activity-based) and token holdings (conviction-based), Snake OS selects for participants who actually use the platform or believe in the project.
