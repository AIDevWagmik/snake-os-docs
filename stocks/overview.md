# The STOCKS App

STOCKS surfaces **xStocks** — tokenized real-world equities issued by [Backed Finance](https://backed.fi) and tradeable on Solana via Jupiter. One xStock = one share of the underlying equity, fully backed 1:1 by collateral held by Backed.

## What you can trade

Snake OS lists **130+ xStocks** covering:

- **Tech mega-caps** — TSLAx, NVDAx, AAPLx, GOOGLx, AMZNx, METAx, MSTRx, MSTRx
- **Financial** — COINx, JPMx, BACx, GSx
- **ETFs** — SPYx (S&P 500), QQQx (Nasdaq-100), GLDx (gold), EWUx (UK)
- **Other sectors** — pharma, consumer, industrials, more

Each entry shows the xStock symbol, the underlying ticker, the company name, and a HALTED badge when trading is paused (after-hours, suspensions, etc.).

## Four category tabs

The STOCKS app filters into:

- **ALL** — every listed xStock
- **TECH** — software, semis, consumer tech
- **FINANCE** — banks, insurance, brokerages
- **ETF** — index funds + thematic ETFs
- **OTHER** — pharma, consumer, industrials, anything not in the above

Tab counts show how many entries each bucket holds — useful if a category temporarily has 0 (Backed source feed degraded).

## How buying works

Tap any xStock card → opens [BUY](../buy/overview.md) pre-filled with that xStock's Solana mint. The swap routes through Jupiter the same way any SPL token swap does. Settlement is on-chain, instantly.

Behind the scenes:
- The xStock mint is an SPL token
- Backed Finance holds the underlying equity 1:1 (audited collateral)
- Snake OS just surfaces the catalog + deep-links to the swap

## What you own

You own an **SPL TOKEN**, not a share. The token is fully backed by Backed Finance's collateral and they handle the wrap/unwrap conversion if you want to redeem to traditional equities.

**Important nuance** (read this if you're new to tokenized equities):

- You DON'T have voting rights on the underlying company
- You DON'T receive dividends directly (Backed handles those via mint-side rebases)
- You CAN'T short the underlying via the xStock
- You CAN sell back to SOL anytime via Jupiter, 24/7
- For tax / legal interpretation, **consult a professional in your jurisdiction** — tokenized equities are a new asset class and rules differ by region

## Why STOCKS exists on a Nokia phone

Because you should be able to trade Tesla from a 3310. That's the bit.

More seriously: Backed's xStocks are one of the cleanest examples of "real-world assets on-chain" — putting them inside Snake OS proves the consumer dApp surface can serve traditional-finance use cases without leaving the Solana stack.

## Sparse liquidity on niche names

xStocks on niche tickers (small-cap, recently-added, weekend hours) often have thin liquidity. Jupiter may struggle to route a big order. This is **expected**, not broken — try a smaller size, or check xstocks.fi for direct routing options.

## Price data

Live xStock prices come from Backed's API + Jupiter's quote engine. The card numbers update on each app open. For deep price history, [MARKET WATCH](../market-watch/overview.md) handles the BTC/ETH/SOL chart view; xStocks don't currently have an in-app chart (they trade enough on-Jupiter that DexScreener has price history if you click through).
