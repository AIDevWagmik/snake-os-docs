# Tokenomics

## Supply

| Metric | Value |
|---|---|
| Total supply | 1,000,000,000 (1B) — fixed by pump.fun protocol |
| On bonding curve at launch | 800M (80%) |
| LP at migration | 200M (20%) |
| Team allocation | **0** (no presale, fair launch) |
| Snake OS treasury initial buy | 5–10% of supply (~50M–100M) on the curve |
| Public float at launch | The remaining ~80–85% |

## Distribution at Launch

Because it's pump.fun fair launch, distribution happens AS the curve fills:

* First buyers get the cheapest entries (early on the bonding curve)
* Waitlist members get a 5–10 minute notification head-start = best curve prices
* Open public follows
* At ~$69k market cap, the curve completes and migrates to PumpSwap

There is no claim portal, no airdrop script, no whitelist pre-allocation. Everyone buys on the curve.

## Post-Launch Distribution

The treasury holds 5–10% initially and grows over time via buybacks. Distribution to users happens through three channels:

### Channel A: Achievement Claims

Active participants claim tokens from the treasury when they unlock achievements. Reward sizes are tiered from 25k to 300k the token per achievement.

### Channel B: PvP Tournament Buybacks (Weekly)

30% of all PvP settle fees that week → buys the token from the open market → distributes to top PvP players by ELO.

### Channel C: Holder Distribution (Weekly)

40% of all PvP settle fees that week → buys the token → distributes to holders weighted by `holdings × days_held` (anti-flipper formula).

### Channel D: Operations + Reserves

Remaining ~30% of fees → treasury operations, payout retry buffer, KMS, infra.

## Locked Liquidity

When the bonding curve completes and the token migrates to PumpSwap, the LP (200M tokens + paired SOL) is **permanently locked by the pump.fun protocol**. No one — including Snake OS — can pull the LP. This is structural rug-protection.

## Vesting

No vesting because there's no team allocation to vest. The treasury's initial 5–10% has no lock — but practically, dumping it would crater the price we depend on for sustainable buybacks. The treasury holds, period.

## Inflation

No inflation. Supply is fixed at 1B. All future distributions come from the treasury (which itself grew from open-market buybacks, not from new mints).
