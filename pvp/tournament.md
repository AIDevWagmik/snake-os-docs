# Weekly Tournament

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141411 (3).png" alt=""><figcaption></figcaption></figure>

The weekly tournament is a **leaderboard-style competition** open to all players. Pay a single entry fee, play as many games as you like during the week, and your best score counts. Top finishers split the prize pot.

## How It Works

1. Open the **DEGEN** screen and tap the **TOURNAMENT** tab
2. Pay the entry fee (0.1 SOL) via your wallet — one entry per wallet per week
3. Play normal snake — every game auto-submits to the leaderboard
4. Your **best score** of the week is your rank score
5. At the end of the week (Sunday 23:59 UTC) the tournament settles and winnings are credited to your `claimable_pvp_sol` balance
6. Claim via the **REWARDS** app alongside your PvP winnings

## Schedule

* **Week:** Monday 00:00 UTC → Sunday 23:59 UTC
* A new tournament opens automatically each Monday
* You can enter any time during the week

## Post-Settle Restart

If a tournament gets settled mid-week (manually by admin, or auto at week end), the system **automatically opens a fresh tournament** for the remaining time in the week + fee tier. You don't need to wait until next Monday to enter the next round.

Backed by migration 027, which replaced the full-row uniqueness constraint with a partial-unique on `status = 'open'` only. Settled and cancelled rows are now allowed to repeat per (week, fee tier), so a new INSERT for a fresh round is permitted after settlement.

## Prize Split

The house takes 5% of the pot. The rest goes to finishers:

### 2 players

| Place  | Share      |
| ------ | ---------- |
| 🥇 1st | 75% of pot |
| 🥈 2nd | 20% of pot |
| House  | 5%         |

### 3 or more players

| Place  | Share      |
| ------ | ---------- |
| 🥇 1st | 65% of pot |
| 🥈 2nd | 25% of pot |
| 🥉 3rd | 5% of pot  |
| House  | 5%         |

4th place and below receive nothing.

## Worked Example (5 players, 0.1 SOL entry each)

| Prize      | Calculation | Payout                      |
| ---------- | ----------- | --------------------------- |
| Pot        | 5 × 0.1     | **0.50 SOL**                |
| 1st (65%)  | 0.50 × 0.65 | **0.325 SOL** (3.25× entry) |
| 2nd (25%)  | 0.50 × 0.25 | **0.125 SOL** (1.25× entry) |
| 3rd (5%)   | 0.50 × 0.05 | **0.025 SOL** (0.25× entry) |
| House (5%) | 0.50 × 0.05 | 0.025 SOL                   |

## Cancellation

If fewer than 2 players enter by week end, the tournament is cancelled and all entry fees are refunded to your `claimable_pvp_sol` balance — no loss on a cancelled week.

## Anti-Cheat

Tournament score submissions go through the same server-side preflight as PvP and solo. Flagged sessions are excluded and do not update your tournament best score.

## Claiming Winnings

Tournament winnings land in the same **claimable\_pvp\_sol** pool as PvP winnings. Open the REWARDS app, tap **CLAIM** on the PvP Pot card, and everything — PvP + tournament — comes out in one transaction. A 3% claim fee applies at withdrawal.
