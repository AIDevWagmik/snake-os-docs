# Wallet Security

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142900.png" alt=""><figcaption></figcaption></figure>

Snake OS never holds your private keys. Your wallet stays on your device.

## What Snake OS Has Access To

* ✅ Your wallet **address** (public)
* ✅ Your wallet's **signature** on the auth message (proves ownership)
* ✅ Your wallet's **signature** on each transaction you approve (sent on-chain by your wallet)
* ✅ Your SOL **balance** (read-only, via public RPC)

## What Snake OS Never Has

* ❌ Your private key
* ❌ Your seed phrase
* ❌ The ability to move your SOL without your approval
* ❌ The ability to sign on your behalf

This is a structural property — not a promise we could break. The signing happens on YOUR device in YOUR wallet. We can only ask; you can always say no.

## What Your Wallet Asks You to Sign

In a normal session you'll be asked to sign:

1. **Auth message** (free, no fee, no transaction) — once per session, cached 1 hour
2. **PvP deposit TX** — actual SOL transfer to treasury, real network fee
3. **Market purchase TX** — actual SOL transfer to treasury, real network fee
4. **PvP claim** — signed message only (the on-chain payout is sent by treasury, not by you)

If your wallet is asking you to sign something that doesn't fit one of these patterns, stop and check. Especially watch for:

* Unexpected SPL token approvals
* Transactions to wallets that aren't our treasury wallet
* "Wallet drainer" patterns (multiple sign requests in a row, foreign program calls)

## If You're Phished

If you connected your wallet to a fake Snake OS clone and signed something:

1. **Disconnect the wallet from all dapps** (Phantom/Solflare settings → disconnect all)
2. **Move your assets to a fresh wallet** if you signed anything malicious
3. **Don't trust** the signed message until you've verified the origin

The real Snake OS is always at `https://snake-os.com`. Anything else is a clone.
