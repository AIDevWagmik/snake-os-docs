# Wagers, Pots & Fees

The exact math behind PvP economics.

## Wager Bounds

* **Minimum:** 0.01 SOL per side
* **Maximum:** 10 SOL per side
* **Combined pot range:** 0.02 SOL to 20 SOL

## The Two-Stage Fee

A small fee is taken in two stages — at settle time and again at claim time.

### Stage 1: Settle Fee (5% of combined pot)

When a match settles:

```
combined_pot = wager_p1 + wager_p2
winner_credit = combined_pot × 0.95
settle_fee = combined_pot × 0.05   →  treasury (funds season prize pool + buybacks)
```

The winner's `claimable_pvp_sol` balance increases by `winner_credit`.

### Stage 2: Claim Fee (5% of credit)

When the winner withdraws their winnings:

```
withdrawal = winner_credit × 0.95
claim_fee  = winner_credit × 0.05   →  treasury
```

### Net Result

```
total_fees = 1 - (0.95 × 0.95) = 1 - 0.9025 = 9.75%
net_to_winner = combined_pot × 0.9025 ≈ 90.25%
```

## Worked Example

You and an opponent each wager **0.5 SOL**:

| Stage | Calculation | Result |
|---|---|---|
| Combined pot | 0.5 + 0.5 | **1.0 SOL** |
| Settle fee (5%) | 1.0 × 0.05 | 0.05 SOL → treasury |
| Winner credit | 1.0 × 0.95 | 0.95 SOL credited |
| Claim fee (5%) | 0.95 × 0.05 | 0.0475 SOL → treasury |
| **Net to winner** | 0.95 × 0.95 | **0.9025 SOL** |
| Total fees | 0.05 + 0.0475 | 0.0975 SOL (9.75%) |

## Where Fees Go

* **30% of settle fees** → Season prize pool (paid to top PvP players each season)
* **Remaining 70% of settle fees** → Treasury (gas, payout retry buffer, future $SNAKE buybacks)
* **Claim fees** → Treasury

Everything flows back to active participants through one of three channels.
