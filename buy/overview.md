# The BUY App

BUY is the Jupiter-routed swap surface inside Snake OS. Paste any Solana mint address (CA) → see live numbers → swap directly from your wallet. Pinned to home alongside SNAKE and WALLET.

## How it works

1. **Paste a CA** (or pick from the POPULAR chips at the top)
2. **Live data loads** — price, 24h change, liquidity, market cap (via DexScreener)
3. **Enter amount** in SOL
4. **Tap BUY** → your wallet prompts you to sign the Jupiter swap transaction
5. **Done** — token lands in your wallet on the same Phantom/Solflare/MWA you connected

## POPULAR chips

The top row of BUY surfaces wrapped versions of the major assets you'd actually want to hold on Solana without leaving the phone:

- **wBTC** (wrapped Bitcoin on Solana)
- **wETH** (wrapped Ethereum on Solana)
- **SOL** (native — usually for sending, not buying)
- Other popular SPL tokens

Tap a chip → mint pre-fills, live data loads, you can size + confirm in seconds.

## Pre-graduation tokens (pump.fun)

BUY automatically detects pump.fun tokens that **haven't graduated yet** (still on the bonding curve, no PumpSwap AMM pool yet). For those, the standard Jupiter route fails. Snake OS routes them to the pump.fun-fallback path so the swap goes through anyway.

If a token is genuinely unrouteable (no liquidity anywhere), BUY surfaces a short error with a link to pump.fun rather than silently failing.

## Fees + slippage

- **No platform fee** — Snake OS doesn't take a cut of swaps. The only fees are Solana network fees (~0.000005 SOL) + Jupiter's standard quote spread.
- **Slippage** is set sensibly by default. High-volatility tokens may need a manual bump — Jupiter surfaces the warning when slippage is likely to fail the quote.

## What BUY is NOT

- **Not for tokenized stocks.** xStocks (TSLAx, NVDAx, AAPLx, etc.) have their own dedicated app — see [STOCKS](../stocks/overview.md).
- **Not for risk scanning.** To assess a token before buying, paste the CA into [ORACLE](../oracle/scanning.md) for an on-chain risk report.
- **Not a portfolio view.** WALLET shows what you hold; BUY is purely the buy flow.

## When BUY fails

- **Wallet rejected** → you cancelled the prompt. Retry.
- **Insufficient SOL** → you don't have enough SOL to cover the buy amount + network fee.
- **No route found** → Jupiter couldn't find liquidity. For pump.fun pre-graduation, the fallback should engage; for everything else this means the token is genuinely illiquid. Skip it.
- **Slippage exceeded** → price moved between quote and execute. Increase slippage tolerance and retry.
