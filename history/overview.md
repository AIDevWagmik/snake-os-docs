# The HISTORY App

HISTORY shows your complete match history inside Snake OS — Solo runs, PvP matches, Challenge attempts, and Tournament entries, all in one timeline.

## What's tracked

For each entry, HISTORY shows:

- **Mode** — Solo / PvP / Challenge (with tier) / Tournament
- **Score** + level reached
- **Outcome** — win / loss / draw / DNF
- **Opponent** (PvP only) — their username + equipped PFP
- **Wager** (PvP / Challenge only) — what was at stake
- **Result** — SOL won/lost, or "claimable" if not yet collected
- **Timestamp**

PvP losses don't show wallet addresses of opponents — usernames only, since the opponent's wallet privacy is theirs to share.

## Filtering

Tap the mode chips at the top to filter:

- ALL
- SOLO
- PVP
- CHALLENGE
- TOURNAMENT

The mode filter persists per session — return to HISTORY and it stays where you left it.

## Claim status visibility

For PvP wins, HISTORY shows whether the SOL has been:

- 🟢 **Claimed** — payout sent to your wallet
- 🟡 **Claimable** — sitting in your claimable balance, ready to claim via [REWARDS](../rewards/pvp-claims.md)
- 🔴 **Failed** — claim attempt errored (rare; usually a transient RPC issue, retry from REWARDS)

For Tournament wins, the status reflects whether the tournament has settled yet — pending settlements show "AWAITING SETTLEMENT" until the admin (or weekly cron) closes the bracket.

## Why HISTORY exists

Two reasons:

1. **Audit trail** — every on-chain action you take in Snake OS is in HISTORY, so you can verify exactly what happened if a match outcome or claim looks off.
2. **Bragging rights** — your win streak, your best Solo score, the Challenge tier you cleared first time. The badge ecosystem in [ACHIEVEMENTS](../rewards/achievements.md) reads from HISTORY for unlock conditions.

## NEW pills

When new matches land since your last visit, the home-grid HISTORY badge shows a count. Opening HISTORY clears the badge. Per-row NEW indicators surface on the most recent entries so you can scan to what's new without scrolling.

## What HISTORY is not

- **Not a leaderboard** — see [LEADERBOARD](../rewards/leaderboard.md) for cross-user rankings.
- **Not a replay system** — Snake OS doesn't store replay data. Match scores + outcomes only.
- **Not editable** — entries are immutable. If something looks wrong (e.g. a settled match shows the wrong score), ping ops in the Telegram support topic.

## Privacy

HISTORY is per-wallet — no one else can see your match history. PvP opponent usernames are visible to you (since you played against them); your username is visible to opponents in their own HISTORY for the same reason.
