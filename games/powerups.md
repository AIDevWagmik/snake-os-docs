# Powerups

Powerups are consumable in-game effects that **spawn during gameplay and activate the instant you collect them**. As of 2026-06, the equip-from-LOCKER flow was removed — powerups now appear as drops alongside food and apply automatically when you eat them. The LOCKER's ITEM tab is gone.

## Available Powerups

| Name | Effect | Approximate Duration |
|---|---|---|
| **GHOST MODE** | Snake passes through walls briefly | ~5 seconds |
| **MAGNET** | Pulls nearby food toward the snake head | ~8 seconds |
| **SPEED BOOST** | Tick rate accelerates — risk/reward | ~6 seconds |
| **SLOW FIELD** | Tick rate slows — easier turns + grid reads | ~6 seconds |

A small icon at the top of the playfield surfaces while a powerup is active so you can see when it's about to expire.

## Where powerups spawn

Powerups spawn occasionally on the board alongside food. Each tick has a small chance of dropping a powerup at a random valid cell. They're rarer than food and don't replace food — they're an additional drop. Some skins/arenas have themed visual variants but the gameplay effect is the same.

## Challenge mode disables powerups

**Challenge mode (all three tiers — EASY / DEGEN / INSANE) does NOT spawn powerups.** The whole point of Challenge is pure skill, no assists, one life. The treasury reservation that backs your wager would be unfair if powerup RNG could swing the outcome.

If a powerup appears during a Challenge run, that's a bug — please ping ops in the Telegram support topic with a screenshot.

## Other modes

| Mode | Powerups spawn? | Powerups affect outcome? |
|---|---|---|
| **Solo** | Yes | Score-only, no SOL at stake |
| **PvP 1v1** | Yes (both players, same RNG seed) | Yes — they're part of competitive play |
| **Challenge** | **No** | N/A — pure skill |
| **Weekly Tournament** | Yes | Yes — affects your best run |

## Anti-cheat note

SPEED BOOST is accounted for in the preflight bot-detection ceiling. The `SCORE_PER_TICK_MAX` cap (76 points/tick) and the `FASTEST_TICK_MS` floor (80ms) both leave headroom for legitimately speed-boosted gameplay at high levels. So real boosted runs aren't flagged; botting beyond physical limits still gets caught.

See [Anti-Cheat & Fair Play](anti-cheat.md) for the full bot-detection model.

## What changed from beta

- **2026-06** — equip-from-LOCKER removed. Powerups are now in-game drops, not a deck you build pre-match.
- **Beta-era LOCKER ITEM tab** is gone. If you previously "owned" powerup items as beta-grant inventory, those entries still exist in the database but no longer surface anywhere in the UI — they don't affect anything.
- **Challenge mode** has always disabled powerups by design. The 2026-06 change makes this enforcement more visible (the powerups simply don't spawn instead of spawning and being inert).
