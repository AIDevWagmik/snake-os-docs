# Security

## Your Keys Stay With You

Snake OS never holds your private key or seed phrase. Your wallet stays on your device. Here's exactly what we access:

| Access | We have it? |
|--------|-------------|
| Your wallet address (public) | ✅ Yes |
| Signature on the auth message | ✅ Yes |
| Signature on each TX you approve | ✅ Yes |
| Your SOL balance (read-only RPC) | ✅ Yes |
| Your private key | ❌ Never |
| Your seed phrase | ❌ Never |
| Ability to move SOL without your approval | ❌ Never |

**What you're asked to sign:**
1. **Auth message** — "Snake OS — sign in" — free, no fee, cached 1 hour
2. **PvP deposit TX** — real SOL to treasury, real network fee
3. **Market purchase TX** — real SOL to treasury, real network fee
4. **PvP claim** — signed message only; the treasury sends SOL to you, not the other way

---

## Origin Lock & Signed Auth

Every API call that changes state goes through two layers:

**Layer 1 — Origin check**
The server verifies the request came from `https://snake-os.com`. Anything else (a clone site, a forged request) gets a 403 before any wallet check happens. Clones can copy our UI but can't use our API.

**Layer 2 — Ed25519 signature**
The server verifies your signed auth message:
- Signature must match your wallet's public key
- Message timestamp must be ≤1 hour old
- On money-moving endpoints: ≤15 minutes old (PvP cancel, claim, market purchase)
- Wallet in message must match wallet in the request

---

## Treasury Escrow

The treasury wallet holds PvP deposits for the duration of a match and releases them on settle/cancel/refund.

| Address | Role |
|---------|------|
| `E1d3nR59ouqB5xc4VV5dGoQ4DcDLNSWSeg8nVbZmqZdT` | Treasury — all deposits in, all payouts out |
| `6suD5pM5eoCLXB2GgtwEmsN3GzBSKvq1yQPwKqeBBLJi` | Dev/admin wallet |

**Treasury private key** is a Cloudflare Worker secret — never logged, never committed, not visible to any frontend.

Race safety: all balance changes use atomic Postgres RPCs and CAS-gated state transitions. Double-spends, double-refunds, and double-cancels are structurally impossible.

---

## Protecting Yourself

- The real Snake OS is always at **https://snake-os.com** — verify the URL before connecting
- Watch for warning signs: unexpected SPL token approvals, transactions to unfamiliar wallets, multiple sign requests in a row
- If you signed something suspicious: disconnect your wallet from all dApps immediately, move assets to a fresh wallet if needed
- Hardware wallets (Phantom + Ledger combo) work on desktop

---

## Reporting Issues

**Bugs** — in-app HELP or Telegram (t.me/snakeOS_sol). Include: what you tried, what happened, browser + wallet, your wallet address.

**Security issues** — Telegram with the word "security" in the message. Responsible disclosure is rewarded.
