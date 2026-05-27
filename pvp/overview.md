# How PvP Works

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141043.png" alt=""><figcaption></figcaption></figure>

**Snake OS PvP is a skill-based 1v1 competition with real-SOL entry fees and prize pools.** Read this entire page before entering.

## Skill-Based Competition — Not a Wager

Snake OS PvP is structurally identical to entry-fee esports tournaments (CS:GO, Hearthstone, fighting-game majors). Specifically:

- **Both players play an identical board.** Same food spawn sequence, same physics, same tick rate, same controls. No RNG determines the winner — only who scores higher.
- **Outcome is purely skill-determined.** Better snake control, better food path selection, better self-collision avoidance. Practice improves your win rate.
- **No house-edge dynamic.** The platform takes a flat tournament fee (3% on settle + 3% on claim) — it is not a counterparty to the match. Both players enter with 50% pre-match win probability.
- **No chance element in winner determination.** Two identical games, the higher score wins.

This is not a betting product. This is a competitive game where the prize pool is funded by entry fees.

## The Flow at a Glance

```
1. Create or Join a match  →  pvp_matches row created (status: waiting)
2. Both players deposit    →  entry fee escrowed to prize-pool wallet
3. Both players ready up   →  status flips to "playing"
4. Both play their game    →  scores submitted, validated
5. Server settles match    →  winner determined by score (CAS-flip to "settled")
6. Winner prize credited   →  claimable_pvp_sol field updated atomically
7. Winner claims prize     →  on-chain payout from prize-pool wallet
```

## Match States

| State       | Meaning                                                                 |
| ----------- | ----------------------------------------------------------------------- |
| `waiting`   | Created, opponent not yet joined                                        |
| `ready`     | Both joined + both deposited entry fees                                 |
| `playing`   | Both clicked READY, match in progress                                   |
| `settled`   | Both scored, winner determined by higher score, tournament fee taken    |
| `cancelled` | Cancelled by creator or auto-cancelled at 5min idle (refunds processed) |

## Economics in 60 Seconds

* Entry fee range: **0.05 SOL minimum, 0.5 SOL maximum** per side
* Combined prize pool = `entry_p1 + entry_p2`
* **3% tournament fee** deducted from the prize pool at settle
* Winner prize credit = `pool × 0.97`
* **Additional 3% claim fee** when winner withdraws to their wallet
* Net winnings to winner = `pool × 0.97 × 0.97` ≈ **94% of combined prize pool**

The tournament fees fund the platform (server, RPC, payouts). The platform is not a counterparty — it has no stake in match outcomes.

## Race Safety

All state transitions use Compare-And-Set (CAS) at the database level:

* Two players can't both claim the same "waiting" slot
* A match can't be cancelled AND settled
* Refunds can't double-fire
* Deposit signatures are uniqueness-indexed — sig replay is rejected

This makes the prize-pool escrow safe even under heavy contention.

## Read These Next

* [Creating a Match](creating.md)
* [Joining a Match](joining.md)
* [Entry Fees & Prize Pools](economics.md)
* [Cancels & Refunds](cancels.md)
