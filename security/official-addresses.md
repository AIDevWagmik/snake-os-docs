# Official Snake OS Wallet Addresses

This page lists the on-chain Solana wallets used by Snake OS and the role each one serves. **Both addresses are public, immutable, and verifiable on any Solana explorer.** Anyone interacting with Snake OS can audit treasury flows directly on-chain.

## Treasury Wallet

**Address:** `E1d3nR59ouqB5xc4VV5dGoQ4DcDLNSWSeg8nVbZmqZdT`

### Function

The treasury wallet is the **escrow + payout custodian** for all real-SOL activity inside Snake OS. It is the destination address for:

- **PvP match deposits** — every player's wager (0.05–0.5 SOL) transfers here when they join a match. Funds are held in escrow until match settle.
- **Challenge mode deposits** — every challenge-tier attempt (0.05–0.20 SOL) transfers here before the game starts.
- **Tournament entry fees** — weekly tournament entries deposit here.
- **Market purchases** — when a user buys a cosmetic skin / theme / arena / badge / PFP, the SOL transfers here.

And it is the source address for:

- **PvP match payouts** — winners receive their net pot share from this wallet on claim.
- **Challenge mode payouts** — winners receive `wager × multiplier` from this wallet on win.
- **Tournament prize distributions** — weekly settle pays top finishers from this wallet.
- **PvP cancellation refunds** — when a match is cancelled before play, both players' deposits are refunded from this wallet.
- **Auto-refunds on validation failures** — if a deposit lands but the match start fails (daily limit, treasury under-funded, etc.), the wager is auto-refunded from this wallet.

### Operational notes

- **Custodial during beta** — private key is a Cloudflare Worker secret, never logged, never committed to source. Only the Worker's signing code can authorize outbound transfers.
- **Hot-wallet target balance** — ≥1.5 SOL during beta, scaling to ≥5 SOL post-launch with alerts at 2 SOL.
- **Post-launch migration** — slated to move to **KMS** (Cloudflare or AWS) or **multi-sig** (2-of-3 signers) for stronger key isolation.
- **Audit trail** — every PvP match settle, challenge payout, tournament prize, and auto-refund is recorded server-side with the on-chain TX signature. Reconciliation against Solscan / Solana Beach is straightforward.

See [Treasury Escrow](treasury.md) for the detailed payout race-safety model.

## Dev / Admin Wallet

**Address:** `6suD5pM5eoCLXB2GgtwEmsN3GzBSKvq1yQPwKqeBBLJi`

### Function

The dev wallet is the **operational / admin account** used by the Snake OS engineering team. Its on-chain role is limited:

- **Admin endpoint signer** — admin-gated routes (e.g. `/api/admin/fund-challenge`, `/api/tournament/settle`, `/api/admin/radar-seed`) require both a shared admin secret header AND a signed-wallet auth message where the signing wallet is in a hardcoded allowlist. This address is in that allowlist.
- **Dev wallet flagged in code** — `DEV_WALLET` constant in `src/lib/mockData.ts` references this address; the wallet is exempt from a small number of UI throttles (rate-limit caps during development, challenge daily-cooldown bypass for testing).

### What this wallet does NOT do

- **No PvP fee accumulation** — house fees from PvP matches flow to the treasury wallet, not here.
- **No treasury withdrawal authority** — this wallet has no signing role over the treasury wallet's private key. Treasury signs are done by the Cloudflare Worker, not by this address.
- **No custody of user funds** — never receives, holds, or signs for user-deposited SOL.

It functions equivalently to an "admin / operator account" pattern — a privileged identifier for back-office endpoints, not a source of funds.

## Verification

All claims above are verifiable on-chain by inspecting the public transaction history of each wallet on any Solana explorer:

- Solscan: paste the address into `https://solscan.io/account/{address}`
- Solana Beach: paste the address into `https://solanabeach.io/address/{address}`
- Solana Explorer: paste the address into `https://explorer.solana.com/address/{address}`

The treasury wallet's transaction history will show:
- Inbound transfers labeled as PvP / challenge / tournament / market deposits
- Outbound transfers to user wallets as match payouts, refunds, and tournament prizes

The dev wallet's transaction history is sparse — it's primarily used as a signing identity for admin endpoints, not as a SOL holder.

## Contact

For label-update inquiries (Solscan, Solana Beach, etc.) or any other on-chain identification questions:

- **Email:** see [Contact](../legal/contact.md)
- **Telegram support topic:** [t.me/snakeOS_sol](https://t.me/snakeOS_sol)
- **Project domain:** [snake-os.com](https://snake-os.com)
- **Official X:** [@SnakeOS_SOL](https://x.com/SnakeOS_SOL)
