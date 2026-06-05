# The COMMUNITIES App

COMMUNITIES is a per-token discussion feed, powered by **CoinCommunities** (the thread system pump.fun integrated after X deprecated its own Communities). Each Solana token gets its own scoped feed of recent posts from holders + watchers.

## Two tabs

### TRENDING
Top communities by recent activity. Each card shows the token symbol, member count, and a rolling post count. Tap a card to expand — the most recent posts for that community load inline.

When new activity is detected in a community you've previously viewed, that card surfaces a **NEW pill** and sorts to the top of the trending list. Tapping the card clears the pill; the card stays at top until you collapse it, then returns to its natural rank.

### LATEST
A cross-community recency feed — the newest posts across ALL tokens, regardless of which community they belong to. Useful for "what's everyone talking about right now" discovery. Each post tags which token's community it came from.

## Why some communities show "no posts yet"

The upstream CoinCommunities per-token messages endpoint is sparse — most communities return empty from that route even when they have thousands of posts. As a workaround, Snake OS:

1. Pulls a wide window (200 posts) from the LATEST cross-community feed
2. **Accumulates** those posts client-side, indexed by token address, across multiple polls
3. Shows whatever's accumulated for that mint when you expand its card

This means **the more time you spend with COMMUNITIES open, the more communities have posts cached**. After a few minutes, the long tail of mints fills in. A genuinely inactive community will still show "no posts yet" because nothing exists upstream to return.

## Read-only for now

Phase 1 is read-only — viewing posts only. Posting + liking would require Twitter OAuth + a linked wallet, which is a separate scope. The CoinCommunities web app at [coincommunities.org](https://coincommunities.org) supports posting if you want to engage on a specific thread.

## Polling cadence

- **TRENDING** — refreshes every 60s (rankings change slowly)
- **LATEST** — refreshes every 30s (recency matters more)

The home-grid notification badge for COMMUNITIES counts new activity across BOTH tabs combined — opening the app and engaging with cards clears the badge.

## Tap the ▶ chip to buy

Each community card has a small ▶ chip that opens [BUY](../buy/overview.md) pre-filled with that mint. Useful when you see a community lighting up and want to take a position immediately.
