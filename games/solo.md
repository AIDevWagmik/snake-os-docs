# Solo Play

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 104506.png" alt=""><figcaption></figcaption></figure>

Open with key **1** or the SNAKE home-screen icon.

## Rules

1. You're a snake moving 1 tile per tick across a grid.
2. Eat food (the glowing pellet) to grow longer and score points.
3. Hit a wall = game over.
4. Hit your own tail = game over.
5. Game speed increases as your snake grows (skill scales).

## Controls

* **D-pad arrows** → turn the snake
* **OK** → pause / resume
* **BACK** → exit to home (game state lost)

## Scoring

* Each food eaten = 1 point + length increase
* Powerups (if equipped) modify scoring temporarily
* High score saves to your profile + the leaderboard
* Solo runs are tagged `mode: 'solo'` in our database

## Difficulty Curve

Game speed scales by level. Recent rebalance softened the high-level curve so survival past L8 is humanly possible:

| Level | Tick speed | Cells per second |
| ----- | ---------- | ---------------- |
| L1    | 480 ms     | 2.1              |
| L5    | 380 ms     | 2.6              |
| L8    | 305 ms     | 3.3              |
| L10   | 275 ms     | 3.6              |
| L13   | 230 ms     | 4.3              |
| L17+  | 180 ms cap | 5.6              |

Old curve capped at 120ms past L15 (8.3 cells/s) — was practically unplayable. New curve introduces a piecewise gentler slope past L8 with a 180ms floor — still fast but the skill ceiling is real.

## Apple Count

Board has **3 apples** through L8, then bumps to **4 apples from L9 onward**. The extra apple at high speed gives tactical options — you can grow + reposition without being forced into impossible chases across an empty board.

## What Solo Earns You

| Reward               | Solo earns it?                    |
| -------------------- | --------------------------------- |
| High score record    | ✅ Yes                             |
| Leaderboard rank     | ✅ Yes                             |
| Achievement unlocks  | ✅ Yes (cosmetic)                  |
| BETA badge           | ✅ Yes (if among first 20)         |
| **the token claims** | ❌ **NO** — requires participation |

Solo play matters for your skill and profile, but does not earn token rewards. See [Reward Eligibility](../rewards/eligibility.md) for why and how to qualify.

## Anti-Cheat

Every solo score is checked server-side with a **synchronous preflight** — impossible scores (faster-than-physically-possible apple eats, suspicious tick rates) are flagged at insert time and excluded from leaderboard + future reward calculations. Botting or scripted input = ban per the Terms.
