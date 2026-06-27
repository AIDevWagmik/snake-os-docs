# Challenge Mode & Tournament

## Challenge Mode

Challenge is a house-funded single-player bet. Pick a tier, pay a wager, beat a target score in one life to win a multiplied payout.

### Tiers

| Tier | Target | Payout | Start level | Tick speed |
|------|--------|--------|-------------|-----------|
| EASY | 6,000 pts | 1.5× wager | LVL 6 | 335ms |
| DEGEN | 10,000 pts | 2× wager | LVL 5 | 352ms |
| INSANE | 14,000 pts | 2.5× wager | LVL 8 | 301ms |

Wager range: **0.05–0.20 SOL**. 1 attempt per tier per 24 hours per wallet.

### How it works

1. Pick tier → pay wager to treasury wallet
2. Server reserves your potential profit from the challenge treasury *before* your game starts
3. Play — **1 life, no powerups**, snake starts fast (elevated level)
4. On death the server reads your score from its records (never trusts the client):
   - **Win** (score ≥ target) → SOL paid directly to your wallet, no claim step
   - **Loss** → your wager stays in the treasury

### Scoring reminder

Challenge mode uses **60 pts per food** (vs. 75 in solo) so the tier targets stay valid as the snake speeds up from a higher start level.

### Challenge treasury

Funded by: manual admin top-ups + 50% of every PvP settle fee. Treasury balance per tier is checked before a game starts — 503 if insufficient.

---

## Weekly Tournament

A weekly leaderboard competition. Pay once to enter, play as many games as you like, and your best score of the week counts.

### How it works

1. Open the TOURNAMENT tab → pay 0.1 SOL entry fee (one entry per wallet per week)
2. Play normal Snake — every game auto-submits
3. Your best score of the week is your rank
4. At Sunday 23:59 UTC the tournament settles; winnings go to `claimable_pvp_sol`
5. Claim via the REWARDS app (same pool as PvP winnings)

### Prize split

**2 players:**
| Place | Share |
|-------|-------|
| 🥇 1st | 75% |
| 🥈 2nd | 20% |
| House | 5% |

**3+ players:**
| Place | Share |
|-------|-------|
| 🥇 1st | 65% |
| 🥈 2nd | 25% |
| 🥉 3rd | 5% |
| House | 5% |

Fewer than 2 players at week end → cancelled, all entry fees refunded.

### Worked example (5 players, 0.1 SOL entry)

| Prize | Amount |
|-------|--------|
| Pot | 0.50 SOL |
| 1st (65%) | 0.325 SOL (3.25× entry) |
| 2nd (25%) | 0.125 SOL (1.25× entry) |
| 3rd (5%) | 0.025 SOL |

### Claiming tournament winnings

Same flow as PvP — winnings land in `claimable_pvp_sol` and are claimed via the REWARDS app with a 3% claim fee.
