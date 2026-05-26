# Who Earns Tokens

See [Reward Eligibility](../rewards/eligibility.md) for the complete policy.

The TL;DR for the project token specifically:

## Three Paths to Earning the token

| Path | What you do | What you earn |
|---|---|---|
| **PvP** | Win PvP matches | SOL winnings + weekly the token prize-pool distributions (top players by ELO) |
| **Market** | Buy any market item | Unlocks all your achievement the token claims (capital qualifies you forever) |
| **Hold** | Hold the token in wallet | Weekly holder buyback distributions (post-launch) |

## What You DO NOT Earn tokens From

* ❌ Solo Snake play (cosmetic badges only)
* ❌ Logging in daily (no streaks, no daily quests)
* ❌ Adding friends (cosmetic achievement only)
* ❌ Sending chat messages (cosmetic achievement only)
* ❌ Referring others (no referral program)
* ❌ Just signing up (no "claim your first 100 tokens" airdrop)

This is intentional. Every reward mechanism known to attract farmers is intentionally absent.

## $SNAKE Holder Gate — HARD RULE

Token reward claims (achievement claims, weekly/season distributions, future buyback distributions) are **only payable to wallets that already hold $SNAKE**.

### Why

1. **Treasury saves rent.** Sending tokens to a fresh wallet that's never held the token requires creating an Associated Token Account, which costs ~0.002 SOL of rent paid by the treasury. At 1000 first-time claimers that's 2 SOL. Holders already have an ATA — transfer skips the create path entirely.

2. **Reinforces the "skin in the game" reward model.** The rewards banner promises `REWARDS = PVP WAGERS · MARKET SPEND · TOKENS HELD`. The holder gate is the enforcement for the third pillar — previously unenforced.

3. **Filters airdrop farmers.** Wallets that have never touched the token have zero conviction. Forcing them to buy first means anyone claiming has at least some position in the project.

### Threshold

**Any non-zero balance qualifies.** Even a small $5 bag is enough to satisfy the holder gate. No minimum threshold beyond `balance > 0`.

### What you'll see if you don't hold

If you try to claim a token reward without holding $SNAKE in your wallet, you'll see:

> **"Token claims are for holders of the token only"**

The claim is blocked with a 403 error and a clear message. Buy any amount of $SNAKE on Jupiter, then come back and claim.

### Pre-launch

Until the $SNAKE mint is deployed and the `SNAKE_MINT_ADDRESS` env var is set on the production server, all token claims return a 503 "token claims not enabled yet" message. Pre-launch UI shows the achievement as locked behind "TOKEN NOT LAUNCHED YET — claim opens at token launch."
