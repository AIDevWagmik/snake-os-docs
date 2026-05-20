# Leaderboard

Global rankings sorted by **best Snake score** (highest snake game score ever). Tab options: DAILY / WEEKLY / ALL TIME (some scopes may be limited during beta).

## What Each Row Shows

* Rank badge (1st/2nd/3rd get medals, others show #X)
* Username
* Wallet (short form: `Abcd…WXYZ`)
* **BETA badge** if OG
* **Equipped badge** if worn
* Best score
* Win/Loss ratio (PvP)
* SOL wagered (lifetime)
* **+ FRIEND** button (if not you)
* "YOU" tag if it's your row

## Ranking Logic

Sorted by `best_score` from `leaderboard_view`. This view computes ranks server-side and exposes:

* `best_score`
* `total_games`
* `pvp_games`
* `pvp_wins`
* `sol_wagered`

PvP and solo both contribute to `best_score`. Stats for `pvp_*` and `sol_wagered` only count PvP matches (solo doesn't move them).

## Seasons

Leaderboard resets at season boundaries (every 90 days). Your lifetime stats stay; the leaderboard view shows the current season only.

## Why Solo Counts for Leaderboard but Not Rewards

Leaderboard = "who's the best Snake player." Solo skill counts.
Rewards = "who's investing in the ecosystem." Only participants (market spend / PvP wagers / $SNAKE holders) qualify.

Two separate axes. See [Reward Eligibility](eligibility.md).
