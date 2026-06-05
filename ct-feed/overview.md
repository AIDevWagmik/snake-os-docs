# The CT FEED App

CT FEED (Crypto Twitter Feed) surfaces real-time X posts from a curated list of tracked KOL (Key Opinion Leader) accounts in the Solana ecosystem. Posts are grouped per KOL and rendered in Snake OS's pixel-text style so you can scan the alpha without leaving the phone.

## Who's tracked

Snake OS curates a fixed list of high-signal Solana traders + builders. Each KOL has their own grouped feed inside CT FEED — tap any KOL row to expand and see their latest posts.

The current set includes accounts like Ansem, Kook, Pow, mistor, Dior, joji, gake, Renzo, bolivian, and Zyaf (full list lives in `KOL_FEED_SOURCES` and can be updated without a deploy). Coverage is curated for SIGNAL — high-volume accounts only, no copy-paste shillers.

## What you see per KOL

- **POSTS tab** — original posts only (retweets filtered out, no noise)
- **QUOTES tab** — quote tweets from that KOL (when relevant)
- **Engagement** — like + reply counts
- **Tap any post** → opens directly on X

## NEW pills

When new posts arrive from a KOL you've recently expanded, that KOL row surfaces a NEW pill with a count. Tap the row to expand → posts load + pill clears. Engagement-driven dismissal: the badge persists until you actually look at the posts, not on a timer.

## How posts get to us

Posts are pulled via rss.app feeds per KOL handle (RSS-to-JSON adapter, free tier caps at 2 live feeds; self-hosted RSSHub is the unlimited path when we outgrow it).

Snake OS proxies these through a Cloudflare Worker that:
- Strips retweets
- Cleans formatting for the pixel-text renderer
- Caches per-KOL responses briefly to avoid hammering rss.app

This means there's a small lag (a few minutes typically) between a KOL posting and it appearing in CT FEED — RSS isn't real-time push, it's polled.

## Why grouped per KOL (not chronological)

CT FEED is grouped per author rather than a chronological cross-account stream so you can read each KOL's recent thinking together. If you want pure recency across all KOLs, the [SNIPE](../snipe/overview.md) app shows transactional activity (KOL wallet buys/sells) which gives a tighter recency picture for active trading.

## CT FEED vs SNIPE

- **CT FEED** = what KOLs are SAYING (X posts)
- **SNIPE** = what KOLs are DOING (on-chain wallet activity)

Use them together: SNIPE shows the action, CT FEED shows the thesis.

## Posts are read-only

You can't reply to or like a post from inside Snake OS — tapping the post opens the original on X, where you handle engagement in the X app or browser as normal.
