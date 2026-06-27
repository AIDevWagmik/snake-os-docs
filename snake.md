# Snake Game

Open with key `1` or the SNAKE home-screen icon.

## Rules

- Move across the grid, eat food to grow and score.
- Hit a wall → game over.
- Hit your own tail → game over.
- Speed increases as you grow.

**Controls:** d-pad arrows to turn, OK to pause/resume, BACK to exit (score lost).

---

## Scoring

| Mode | Points per food | Points per tick |
|------|----------------|-----------------|
| Solo | 75 | +1 |
| Challenge | 60 | +1 |

Challenge uses a lower per-food value so the tier targets (6k / 10k / 14k) remain meaningful at higher speeds.

---

## Difficulty Curve

| Level | Tick speed |
|-------|-----------|
| L1 | 480ms |
| L5 | 380ms |
| L8 | 305ms |
| L10 | 275ms |
| L13 | 230ms |
| L17+ | 180ms (floor) |

Apple count: 3 from L1–L8, then 4 from L9 onward.

---

## Skins

Skins change your snake's color and head/body texture. Equipped in the LOCKER app.

**Free skins** (granted to all new accounts):
- CLASSIC GREEN, TOXIC, SHADOW, LAVA SNAKE, SOL VIPER

**Market skins** — purchasable in the MARKET with SOL. Prices shown in-app.

---

## Arenas

Arenas are background themes for the game grid.

**Free arenas:**
- CLASSIC GRID (default), JUNGLE RUINS

**Market arenas** — purchasable in the MARKET.

Arenas use a stretched-floor render with 10% body bleed and 10% corner bleed for a full-screen feel on every aspect ratio.

---

## Powerups

Powerups spawn in-game and apply on pickup — no equipping required.

| Powerup | Effect |
|---------|--------|
| Speed Boost | Temporary tick-rate increase |
| Shield | Next wall/tail hit forgiven |
| Double Score | 2× points per food for a short window |
| Shrink | Removes several tail segments |

Powerups do **not** appear in Challenge mode (1-life runs are powerup-free by design).

---

## Anti-Cheat

Every score is validated server-side before it saves:

- **SCORE_PER_TICK_MAX = 76** — a single tick can't yield more than food-value + 1 tick-point. Superhuman scores are rejected at insert time.
- **FASTEST_TICK_MS = 80** — timestamps between moves are checked; bot-speed input is flagged.
- **Bot-detection score** — async session analysis runs alongside every game. Flagged sessions are excluded from leaderboard, rewards, and PvP settlement.
- **Session binding** (Challenge/PvP) — scores are read from the server's `game_sessions` record, never from client-supplied values.

> Scripted input, bot assistance, or intentional score exploitation = permanent ban with no refund of in-flight wagers.
