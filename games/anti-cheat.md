# Anti-Cheat & Fair Play

![HISTORY app — every game session is logged + scoring is validated server-side](../images/screenshots/game-history-app.png)

Snake OS uses both **synchronous preflight** and **async session analysis** to detect cheating.

## Synchronous Preflight (At Score Submission)

When your game ends and the score posts to `/api/scores/solo`, `/api/pvp/score`, `/api/tournament/score`, or `/api/challenge/settle`:

* Server checks game length vs minimum possible time for that score
* Validates tick rate (≥80ms floor — accounts for SPEED BOOST at max level)
* Flags impossible "eat rates" (score per tick beyond physical maximum: 76 pts/tick)
* Rejects scores that violate any check before they hit the database

This closes the TOC/TOU window where a cheater could potentially insert a forged score and have it briefly visible.

## Async Session Analysis

After insertion, every game session is queued for deeper analysis:

* Input timing patterns (bot vs human signatures)
* Mouse/touch movement entropy
* Reaction-time distribution
* Cross-session anomalies (suspiciously identical session shapes)

Flagged sessions are marked `is_flagged=true` and excluded from PvP scoring + reward eligibility.

## Bans

Per the Terms:

* **Botting / scripted input** → immediate permanent ban, no refund of in-flight stakes
* **Wash-trading PvP** (matches with yourself via a second wallet) → ban + winnings clawed back
* **Client modifications** to bypass checks → ban + audit
* **Exploit reports** → bug-bounty rewards (responsible disclosure)

If you think your account was banned in error, report it in our support topic on [Telegram](https://t.me/snakeOS_sol) with your wallet address — every ban triggers an admin audit log we can review.
