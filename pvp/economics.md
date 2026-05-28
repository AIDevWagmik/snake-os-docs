# Entry Fees & Prize Pools

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141226.png" alt=""><figcaption></figcaption></figure>

The exact math behind PvP economics. Snake OS PvP is a skill-based 1v1 — both players pay an entry fee into a combined prize pool, and the higher score wins. The platform takes a flat tournament fee (it is not a counterparty to the match).

## Entry Fee Bounds

* **Minimum:** 0.05 SOL per side
* **Maximum:** 0.5 SOL per side
* **Combined prize pool range:** 0.10 SOL to 1.0 SOL

## The Two-Stage Fee

A small tournament fee is taken in two stages — at settle time and again at claim time.

### Stage 1: Settle Fee (3% of prize pool)

When a match settles:

```
prize_pool    = entry_p1 + entry_p2
winner_credit = prize_pool × 0.97
settle_fee    = prize_pool × 0.03   →  treasury (funds season prize pool, challenge treasury + buybacks)
```

The winner's `claimable_pvp_sol` balance increases by `winner_credit`.

### Stage 2: Claim Fee (3% of credit)

When the winner withdraws their winnings:

```
withdrawal = winner_credit × 0.97
claim_fee  = winner_credit × 0.03   →  treasury
```

### Net Result

```
total_fees = 1 - (0.97 × 0.97) = 1 - 0.9409 = 5.91%
net_to_winner = combined_pot × 0.9409 ≈ 94.09%
```

## Worked Example

You and an opponent each enter with **0.5 SOL**:

| Stage             | Calculation   | Result                |
| ----------------- | ------------- | --------------------- |
| Prize pool        | 0.5 + 0.5     | **1.0 SOL**           |
| Settle fee (3%)   | 1.0 × 0.03    | 0.03 SOL → treasury   |
| Winner credit     | 1.0 × 0.97    | 0.97 SOL credited     |
| Claim fee (3%)    | 0.97 × 0.03   | 0.0291 SOL → treasury |
| **Net to winner** | 0.97 × 0.97   | **0.9409 SOL**        |
| Total fees        | 0.03 + 0.0291 | 0.0591 SOL (5.91%)    |

## Where Fees Go

* **30% of settle fees** → Season prize pool (paid to top PvP players each season)
* **50% of settle fees** → Challenge treasury (funds Challenge mode payouts)
* **Remaining 20% of settle fees** → Treasury (gas, payout retry buffer, future token buybacks)
* **Claim fees** → Treasury

Everything flows back to active participants through one of three channels.
