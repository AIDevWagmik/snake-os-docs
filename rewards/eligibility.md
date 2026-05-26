# Reward Eligibility — Read This

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142800.png" alt=""><figcaption></figcaption></figure>

This is the most important page in this entire GitBook for anyone planning to earn from Snake OS.

## The Policy in One Sentence

> **token rewards are only claimable by active participants — users who have spent in the market, wagered in PvP, or hold the token in their wallet.**

Solo-only accounts that never spend, wager, or hold can play and earn cosmetic badges, but cannot claim the token rewards.

## Why This Policy Exists

Without this gate, Snake OS would attract one specific user type: **airdrop farmers**. Accounts that sign in once, play 100 solo games, claim every grind achievement, and dump tokens at launch — bringing nothing to the ecosystem.

We chose a different audience: people who play because they like the game and people who hold the token because they believe in the project. Both groups have skin in the game; both deserve to be paid back.

## How You Qualify

Any **one** of these qualifies you forever:

### A. Make a Market Purchase

Buy literally anything in the MARKET app — even a 0.02 SOL powerup converts you from spectator to participant. Once you qualify, you stay qualified.

### B. Place a PvP Wager

Deposit into any PvP match (even one you go on to lose). The on-chain deposit signature is what counts — joining a lobby without depositing does not qualify.

### C. Hold the token (Post-Launch Only)

Once the token is live, holding any amount in your connected wallet qualifies you. Pre-launch this check is N/A — there's no token to hold yet.

## How the Gate Actually Works

When you tap CLAIM on an achievement:

1. Server checks `hasParticipated(your_user_id)`
2. If yes → claim proceeds → the token credited to your balance
3. If no → `403 { error: "participation_required" }` → frontend shows the lock icon + banner

The check is re-evaluated on every claim attempt. So:

* Achievement unlocked while you're a non-participant? → It stays unlocked. Banner shows it's locked behind participation.
* You then make a market purchase or PvP deposit? → The same achievement is now claimable. Eligibility is retroactive within the gate.

## What Solo Players Get (Without Token Rewards)

Even non-participants get a lot:

* ✅ Full access to solo Snake game forever
* ✅ Leaderboard rankings (best-score driven)
* ✅ Achievement unlocks (cosmetic badges)
* ✅ BETA badge if among first 20
* ✅ Profile, friends, chat, ORACLE scans (free), DEGEN feed, SNIPE feed
* ✅ Full market browsing
* ❌ the token claims

## What Participants Get (Everything)

* All of the above, PLUS:
* ✅ Achievement the token claims (all tiers)
* ✅ PvP claim winnings (already participant by definition)
* ✅ Season prize eligibility (if also meeting MIN\_MATCHES/WAGER floors)
* ✅ Future token buyback distributions (post-launch, weight based on activity + holdings)

## TL;DR

| You...                            | You earn...                                                                   |
| --------------------------------- | ----------------------------------------------------------------------------- |
| Play 100 solo games               | Cosmetic achievements, leaderboard rank, no the token                         |
| Buy a 0.02 SOL powerup            | All of above + retroactively claim all the token achievements you've unlocked |
| Play a 0.01 SOL PvP match         | Same as above                                                                 |
| Hold the token post-launch        | Same as above + future buyback distributions                                  |
| Play nothing, just hold the token | token buyback distributions, no achievements                                  |

Aligned. Honest. Hard to farm.
