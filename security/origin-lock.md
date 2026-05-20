# Origin Lock & Signed Auth

The two most important security mechanisms in Snake OS.

## Origin Lock

Every API call that changes state on our backend (creating a match, purchasing, claiming, etc.) goes through `requireSignedWallet()`. Before ANY signature check, the server verifies the request's **Origin header** is exactly:

* `https://snake-os.com` (production), OR
* `http://localhost:5173` (dev only, and only when `NODE_ENV !== production`)

**Anything else gets a 403 immediately.**

## What This Defends Against

Clone websites that scrape our bundle and serve it from `snake-os-rugpull.com` or `snak3-os.io`. Even if they perfectly replicate our UI:

* Their requests come from THEIR origin
* Our server rejects them with 403
* They can't drain users' wallets using our bundle's code

A clone hosting our JS still can't call our API. The strongest anti-clone defense available.

## Signed Wallet

After origin passes, the server verifies an ed25519 signature on:

```
"Snake OS - sign in
Wallet: <wallet_address>
Issued: <ISO timestamp>
Valid for: 1 hour"
```

* The signature must verify with the claimed wallet's public key
* The `Issued` timestamp must be ≤ 1 hour old (≤ 15 minutes for money-moving endpoints)
* The wallet in the message must match the wallet in the request body (rejects body-wallet ≠ signed-wallet mismatches)

## STRICT\_MAX\_AGE\_MS (15 Minutes)

For money-moving endpoints (`pvp/cancel`, `rewards/pvp-claim`, `market/purchase`), the signature must be ≤ 15 minutes old, not the standard 1 hour. This means:

* Sensitive actions re-prompt for signature if your session is old
* A stolen session has a much narrower window of damage

## Why Both Together

| Layer | Defends against |
|---|---|
| Origin Lock | Clone websites + unauthorized cross-origin calls |
| Signed Wallet | Spoofed wallet addresses / API forgery |
| STRICT\_MAX\_AGE\_MS | Replay of old sessions on money endpoints |

All three checks run on every mutating endpoint. Defense-in-depth.
