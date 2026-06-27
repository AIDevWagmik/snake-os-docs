# Tokenomics

## Supply

| Metric | Value |
| ------ | ----- |
| Total supply | 1,000,000,000 (1B) — fixed by pump.fun protocol |
| On bonding curve at launch | 800M (80%) |
| LP at migration | 200M (20%) |
| Team allocation | **0** (no presale, fair launch) |
| Snake OS treasury initial buy | 5–10% of supply (~50M–100M) on the curve |
| Public float at launch | The remaining ~80–85% |

## Distribution at Launch

Because it's a fair launch, distribution happens as the curve fills:

* First buyers get the cheapest entries (early on the bonding curve)
* Open public follows
* At ~$69k market cap, the curve completes and migrates to PumpSwap

There is no claim portal, no airdrop script, no whitelist pre-allocation. Everyone buys on the curve.

## Post-Launch Distribution

The treasury holds 5–10% initially and grows over time via buybacks. Distribution to users happens through four channels:

### Channel A: BITS Burn Pool (Weekly)

The primary distribution mechanism post-launch. Every week:

* **1,000,000 tokens per week** allocated from treasury
* Supplemented by a share of PvP/market SOL fees converted via open-market buybacks
* Each user's share = `their BITS / total BITS` × weekly pool
* BITS are earned across all Snake OS apps (gaming, social, trading, exploring) and through achievement badge claims
* Proportional — the more you participate, the larger your weekly share

BITS accumulate during beta. The exchange opens at launch.

### Channel B: PvP Tournament Buybacks (Weekly)

30% of all PvP settle fees that week → buys tokens from the open market → distributes to top PvP players by performance.

### Channel C: Holder Distribution (Weekly)

40% of all PvP settle fees that week → buys tokens → distributes to holders weighted by `holdings × days_held` (anti-flipper formula).

### Channel D: Operations + Reserves

Remaining ~30% of fees → treasury operations, payout retry buffer, infra.

## Locked Liquidity

When the bonding curve completes and the token migrates to PumpSwap, the LP is **permanently locked by the pump.fun protocol**. No one — including Snake OS — can pull the LP. Structural rug-protection.

## Vesting

No vesting because there's no team allocation to vest. The treasury's initial buy has no lock — but the protocol depends on sustained buybacks, so dumping it would crater the very price that funds distributions. The treasury holds.

## Inflation

No inflation. Supply is fixed at 1B. All future distributions come from the treasury (which grows from open-market buybacks, not new mints).
