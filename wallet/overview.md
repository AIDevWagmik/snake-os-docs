# The WALLET App

The WALLET app is your in-Snake-OS view of the Solana wallet you connected. It's pinned to the home grid alongside SNAKE and BUY so balance + recent activity are one tap away from wherever you are.

## What WALLET shows

- **SOL balance** — live, refreshed each time you open the app
- **Equipped PFP** — the avatar you picked in [LOCKER](../locker/overview.md). If you have a market-purchased badge equipped, it renders inline next to your username.
- **Username** — picked once in [Getting Started](../getting-started/connecting-wallet.md)
- **Recent on-chain activity** — your last several Solana transactions (PvP deposits, market purchases, claims, etc.)
- **Send / Receive** — opens the standard wallet flow for moving SOL or SPL tokens in/out

## Supported wallets

WALLET reads from whichever Solana wallet you connected at sign-in. Snake OS supports:

- **Phantom** — extension on desktop, native iOS app, universal links on mobile, in-app browser on Android
- **Solflare** — same surfaces as Phantom, plus Solflare's Android in-app-browser redirect
- **Mobile Wallet Adapter (MWA)** — for Solana Mobile Seeker / Seed Vault and any MWA-compatible Android wallet

If your wallet isn't listed, see [Connecting Your Wallet](../getting-started/connecting-wallet.md) for the supported set + adapter chain.

## What WALLET does NOT do

- **Not a custodial wallet.** Snake OS never holds your private key. The app reads balances + relays signed transactions to your real wallet — that's it.
- **Not a swap surface.** For buying tokens, use [BUY](../buy/overview.md). For staking / yield / lending, use the underlying wallet directly.

## Switching wallets

Disconnect via the WALLET app's menu, then sign in with a different wallet. Your username, BETA badge, equipped cosmetics, and game history are tied to the wallet address — switching wallets switches accounts.

The signed auth credential is cached per-wallet in your browser's `sessionStorage`. Signing out of one wallet doesn't affect another wallet's session on the same device.

## Security notes

- Every API call that moves SOL or changes state requires a fresh signed auth message — see [Origin Lock & Signed Auth](../security/origin-lock.md).
- The signed auth expires after 1 hour (15 min on money-moving endpoints). When it expires, you'll be asked to re-sign before the next transaction.
- Snake OS rejects requests that don't originate from `snake-os.com` — clones can render the UI but can't talk to our backend.
