# Buying via Jupiter

DEGEN has a built-in Jupiter swap modal so you can buy any listed token without leaving Snake OS.

## How to Buy

1. In DEGEN feed, tap the token you want.
2. Tap **BUY**.
3. The Jupiter swap modal opens, pre-filled with:
   * Input: SOL
   * Output: the selected token
4. Enter the SOL amount or use the quick presets (0.05 / 0.1 / 0.5 / 1).
5. Set slippage (default 1%, options 0.5%, 1%, 3%, 10%).
6. Tap **SWAP**.
7. Modal re-quotes immediately for the freshest route.
8. Wallet popup → approve the swap transaction.
9. Confirmation includes a Solscan link to view the TX.

## Selling

Same modal, opposite direction:

1. From the token's detail view, tap **SELL**.
2. Quick presets are now percentages (25% / 50% / 75% / **MAX**).
3. MAX uses your FULL token balance — no haircut, no dust.

## Behind the Scenes

* Jupiter v1 lite-api (`lite-api.jup.ag/swap/v1/*`)
* Fresh quote re-fetched immediately before every swap (avoids stale-quote failures)
* 15-second background quote refresh keeps the displayed RECEIVE amount live
* Dynamic compute unit limit + high priority fee for reliable inclusion

## DYOR Disclaimer

> ⚠ **Memecoin prices can collapse to zero in seconds.** Snake OS only routes the swap through Jupiter — it does NOT vet, endorse, or guarantee any token. Always research the contract, holders, and liquidity before buying. Use ORACLE to scan first.

We're a tool, not a financial advisor.
