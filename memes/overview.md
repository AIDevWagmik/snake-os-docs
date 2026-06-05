# The MEMES App

MEMES is a vertical-scroll meme card feed inside Snake OS. Pure entertainment — no trading angle, no analytics. The phone needed a meme app.

## How it works

- Scroll vertically through a curated set of pixel-style memes
- Tap any meme → opens fullscreen
- Closes with the BACK softkey, ESC on keyboard, or tap outside

## What's in the feed

The meme set is **shuffled on each visit** so opening MEMES feels different each time. The bundled set covers:

- Snake OS in-jokes (the retro phone aesthetic, the closed beta, etc.)
- Solana crypto culture references
- Pump.fun lore
- General degen energy

New memes get added on deploys — the feed is curated, not user-submitted (Phase 1).

## NEW pills

When new memes ship on a deploy, the home-grid MEMES badge surfaces a count. Opening MEMES clears the badge; individual memes that arrived since your last visit get a small NEW indicator on the card itself.

The badge dismissal is **engagement-driven** — entering the app counts as "seen." The per-card NEW indicator clears after a few seconds of in-app activity.

## Performance

Meme images are lazy-loaded — only the visible cards download initially. This keeps MEMES snappy even when the bundled set grows. The asset folder is WebP-converted as of 2026-06 so each card is ~150-300 KB instead of the 1-2 MB the PNG-era cards used to be.

## What MEMES is not

- Not user-generated. There's no submit / upload flow.
- Not monetized. No ads, no fees, no token mechanics.
- Not search-able. It's a vertical scroll, intentionally lo-fi.
