# BITS & Rewards

BITS are an off-chain soft currency earned by using Snake OS. They accumulate in your account now and convert to tokens at launch via a weekly burn pool. There is no participation gate — anyone can earn BITS.

---

## How to Earn BITS

BITS are awarded for almost everything you do on Snake OS. All activity is tracked server-side.

| Activity | Notes |
|----------|-------|
| Playing Snake (solo/PvP/challenge/tournament) | Per session, daily cap |
| Winning a PvP match | Per win |
| Entering a tournament | Per entry |
| Making a market purchase | Per purchase |
| Sending a chat message | Per message, daily cap |
| Running an ORACLE session | Per session, daily cap |
| Scanning a unique CA in ORACLE | Once per CA per wallet |
| Opening RADAR | Per session, daily cap |
| Buying or selling on Jupiter (BUY/DEGEN) | Per confirmed swap |
| Reacting with emotes in MEMES | Per emote |
| Checking the leaderboard | Per visit, daily cap |
| Claiming an achievement | One-time, per achievement |

**Daily caps** — most activities have a daily cap enforced by a unique key per wallet + activity + date. Hitting the cap doesn't error — it just doesn't award more BITS that day.

---

## Achievements & BITS Rewards

Achievements are unlocked by gameplay milestones. Claim them in the BADGES app — no participation gate, anyone can claim their unlocked achievements.

| Achievement | BITS | Condition |
|-------------|------|-----------|
| First Bite | 250 | Play your first game |
| 100 Coins | 500 | Score 100 pts in solo |
| PvP Winner | 1,500 | Win a PvP match |
| Survivor | 1,500 | Survive 200+ ticks in one game |
| Memeoor | 1,000 | Send 20 emote reactions |
| Tournament Entrant | 1,000 | Enter your first tournament |
| Chat Regular | 1,500 | Send 50 chat messages (all time) |
| Oracle Explorer | 2,000 | Complete 10 ORACLE sessions |
| RADAR Watcher | 2,500 | Visit RADAR 7 days in a row |
| Friendly | 2,000 | Have 5 friends |
| Rematch King | 3,000 | Win 3 PvP rematches |
| Skin Collector | 2,500 | Own 5 skins |
| Degen Trader | 3,000 | Buy and sell on Jupiter |
| High Roller | 6,000 | Wager 2 SOL total (PvP/challenge) |
| Challenge Conqueror | 6,000 | Win all 3 challenge tiers (EASY + DEGEN + INSANE) |
| Market badges | 1,500–2,500 | Purchase a cosmetic badge from the Market |
| God Tier | 10,000 | Finish top 3 on the leaderboard |
| Whale | 12,000 | Wager 10 SOL total (PvP/challenge) |

**Auto-unlocks** — some achievements unlock automatically when you hit the condition server-side. Others show as available to claim once you've met the threshold.

---

## Leaderboard BITS

The leaderboard has three tabs:

| Tab | Ranking | Resets |
|-----|---------|--------|
| SOLO | Best solo score this week | Weekly |
| PVP | Most PvP wins this week | Weekly |
| SEASON | Best score across all modes this month | Monthly |

**Claiming leaderboard BITS** — if your name appears in the top 10, a **CLAIM BITS** button appears on your row. Tap it to collect. One claim per wallet per period (weekly for SOLO/PVP, monthly for SEASON).

| Rank | BITS |
|------|------|
| 🥇 1st | 5,000 |
| 🥈 2nd | 3,000 |
| 🥉 3rd | 1,500 |
| 4th | 800 |
| 5th | 500 |
| 6th–7th | 300 |
| 8th–10th | 150 |

---

## PvP SOL Claims

PvP winnings (PvP matches + tournament prizes) accrue in your `claimable_pvp_sol` balance and are claimed separately via the REWARDS app.

1. Open REWARDS → see the **PvP Pot** card with your claimable balance
2. Tap CLAIM → wallet signs a message (no SOL from you)
3. Treasury sends the payout on-chain — you receive balance × 0.97 after the 3% claim fee
4. Confirm via the TX signature shown in the app

**15-minute auth window** — claim endpoints require a signature ≤15 min old. You'll be re-prompted if it's stale.

If claim fails: your balance is restored atomically. Safe to retry.

---

## Token Launch

BITS accumulate now and carry forward. When the token launches, a weekly burn pool opens (2,000,000 tokens/week). Users burn their BITS for a proportional share of that week's pool. The more BITS you've stacked, the larger your share.

> The token is **not live yet**. The REWARDS screen shows a placeholder for the exchange. No action needed until launch.
