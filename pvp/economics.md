# Wagers, Pots & Fees

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141226.png" alt=""><figcaption></figcaption></figure>

The exact math behind PvP economics.

## Wager Bounds

* **Minimum:** 0.05 SOL per side
* **Maximum:** 0.5 SOL per side
* **Combined pot range:** 0.10 SOL to 1.0 SOL

## The Two-Stage Fee

A small fee is taken in two stages — at settle time and again at claim time.

### Stage 1: Settle Fee (3% of combined pot)

When a match settles:

```
combined_pot = wager_p1 + wager_p2
winner_credit = combined_pot × 0.97
settle_fee = combined_pot × 0.03   →  treasury (funds season prize pool, challenge treasury + buybacks)
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

You and an opponent each wager **0.5 SOL**:

| Stage             | Calculation   | Result                |
| ----------------- | ------------- | --------------------- |
| Combined pot      | 0.5 + 0.5     | **1.0 SOL**           |
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
