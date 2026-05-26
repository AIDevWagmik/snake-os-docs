# Buying via Jupiter

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142232.png" alt=""><figcaption></figcaption></figure>

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

## Swap Result Screen

After you confirm in your wallet, the modal shows one of four states:

| State | Meaning | What to do |
|---|---|---|
| **CONFIRMING…** | TX broadcast, awaiting confirmation | Wait — typically 2-4 seconds now |
| **✓ CONFIRMED** | Swap landed on-chain successfully | Solscan link visible, CLOSE |
| **✗ SWAP FAILED** | TX reverted on-chain (with reason) | Use **↻ TRY AGAIN** button — restores form with amount + slippage intact |
| **⚠ STATUS UNKNOWN** | Couldn't verify in time — tx may still settle | Check Solscan first BEFORE retrying (avoids double-spend) |

### Try Again on Failure

If the swap fails (slippage exceeded, route stale, etc.), the result screen now has a **↻ TRY AGAIN** button. Clicking it:

- Resets the result state
- Keeps your amount, slippage, and most recent quote intact
- One tap to retry instead of having to leave the app and re-enter everything

The button only appears on `FAILED` state — never on `UNKNOWN` (where retry could double-spend if the original tx actually landed) and never on `CONFIRMED`.

### Faster Confirmation

Previous design waited the full WebSocket timeout (~30s) before any polling. New design races the WS subscription against an immediate HTTP poll loop — whichever returns first wins. Typical confirmation is now **2-4 seconds** instead of 20-30. Accepts Solana's `processed` commitment as good-enough for UX (practically never reorgs for user-signed transfers).

## Behind the Scenes

* Jupiter v1 lite-api (`lite-api.jup.ag/swap/v1/*`)
* Fresh quote re-fetched immediately before every swap (avoids stale-quote failures)
* 15-second background quote refresh keeps the displayed RECEIVE amount live
* Dynamic compute unit limit + high priority fee for reliable inclusion
* Pre-simulation before signing (per Phantom's recommended pattern — surfaces preflight errors before the wallet popup)
* Three-state confirmation: CONFIRMED / FAILED / UNKNOWN (never silently fails)

## DYOR Disclaimer

> ⚠ **Memecoin prices can collapse to zero in seconds.** Snake OS only routes the swap through Jupiter — it does NOT vet, endorse, or guarantee any token. Always research the contract, holders, and liquidity before buying. Use ORACLE to scan first.

We're a tool, not a financial advisor.
