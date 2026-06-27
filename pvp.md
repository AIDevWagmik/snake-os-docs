# PvP — Real-SOL 1v1

PvP is skill-based wagering. Both players play identical boards (same food spawns, same physics, same tick rate). No RNG determines the winner — the higher score wins.

---

## How a Match Works

```
1. Create or join a match → entry fee escrowed to treasury wallet
2. Both players deposit    → status: "ready"
3. Both click READY        → match goes "playing"
4. Both play their game    → scores submitted and validated server-side
5. Server settles          → winner determined by score (CAS-safe)
6. Winner's balance credited → claimable_pvp_sol updated atomically
7. Winner claims via REWARDS → on-chain payout from treasury
```

---

## Entry Fees & Payout

| | |
|---|---|
| Min wager | 0.05 SOL per side |
| Max wager | 0.50 SOL per side |
| Prize pool | p1 + p2 |
| Settle fee | 3% of pool → treasury |
| Claim fee | 3% of credited balance |
| **Net to winner** | **pool × 0.97 × 0.97 ≈ 94.1%** |

**Worked example — both wager 0.5 SOL:**

| Step | Amount |
|------|--------|
| Prize pool | 1.0 SOL |
| Settle fee (3%) | −0.03 SOL |
| Winner credited | 0.97 SOL |
| Claim fee (3%) | −0.029 SOL |
| **Winner receives** | **0.9409 SOL** |

> 50% of settle fees fund the Challenge mode treasury.

---

## Creating a Match

1. Open PVP → tap CREATE
2. Set your wager (0.05–0.50 SOL)
3. Confirm → your wallet sends the deposit to the treasury wallet
4. Share the match link or let someone find your open slot in the lobby

---

## Joining a Match

1. Open PVP → browse the LOBBY tab
2. Tap a waiting match that fits your wager budget
3. Confirm deposit → both sides are now "ready"

Only one player can claim an open slot (race-safe CAS on `status='waiting'`).

---

## Cancels & Refunds

You can cancel a waiting or ready match before both players have clicked READY.

- Both deposited sides are refunded to `claimable_pvp_sol`
- Cancel is CAS-gated: a match that's already been settled can't also be cancelled
- If a match stays stuck in `ready` state (opponent goes offline), it auto-cancels after 5 minutes

---

## Rematches

After a settled match, either player can tap REMATCH. This creates a fresh match with the same wager and drops a `rematch_invite` notification to the opponent. Notifications poll every 10 seconds.

---

## Claiming Winnings

1. Open REWARDS app
2. Tap the **PvP Pot** card — shows your claimable balance
3. Tap CLAIM → wallet signs a message (no SOL from you)
4. Treasury sends the payout on-chain
5. 3% claim fee deducted, remainder arrives in your wallet

**Strict 15-min auth window on claims** — if your auth is older than 15 minutes you'll be re-prompted to sign before claiming.

If claim fails: balance is restored atomically, safe to retry. If it fails repeatedly, report in Telegram with the timestamp.

---

## Match States

| State | Meaning |
|-------|---------|
| waiting | Created, opponent not yet joined |
| ready | Both joined + deposited |
| playing | Both clicked READY, in progress |
| settled | Scores submitted, winner determined |
| cancelled | Cancelled or auto-expired |
