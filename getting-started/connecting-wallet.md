# Connecting Your Wallet

Snake OS supports three wallet paths:

## Desktop / Laptop

| Wallet | How |
|---|---|
| **Phantom** | Install [Phantom](https://phantom.app) browser extension → click CONNECT on Snake OS → approve in popup |
| **Solflare** | Install [Solflare](https://solflare.com) extension → CONNECT → approve |
| **Backpack** | Install [Backpack](https://backpack.app) → CONNECT → approve. Backpack will appear as a Phantom-compatible option |

## iOS

| Wallet | How |
|---|---|
| **Phantom** | Open Safari → snake-os.com → tap CONNECT → choose Phantom → confirm in Phantom app (universal link) |
| **Solflare** | Same flow via Solflare app |
| **In-app browsers** | You can also open snake-os.com directly inside Phantom or Solflare's built-in browser. Works the same way |

## Android

You'll see four options in the wallet picker. Two recommended paths depending on your setup:

### Option 1 — Mobile Wallet Adapter (Solana Mobile Seeker users)

If you're on a **Solana Mobile Seeker** with **Seed Vault**, or any Android device with an MWA-compatible wallet installed:

1. Open Chrome → snake-os.com → tap **CONNECT**
2. Tap **Mobile Wallet Adapter**
3. Android shows the system wallet picker → choose Seed Vault / Phantom / Solflare / Backpack
4. Approve the connection inside the wallet → returned to Snake OS connected

MWA uses Android's native intent system and biometric prompts — most secure path on Solana Mobile.

### Option 2 — Phantom / Solflare / Backpack (other Android users)

If you don't have a Seeker or MWA-compatible wallet, the bare wallet buttons auto-redirect you into the wallet's own in-app browser (Android Chrome blocks the direct app-launch that iOS allows):

1. Open Chrome → snake-os.com → tap **CONNECT**
2. Pick **Phantom**, **Solflare**, or **Backpack**
3. You'll be redirected into the wallet's app, with snake-os.com pre-loaded inside its built-in browser
4. Inside the wallet's browser, tap **CONNECT** again → approve
5. Done

One extra tap vs. iOS, but reliable on every Android browser we've tested.

### If the redirect doesn't fire

Some Android browsers (Samsung Internet, older Chrome versions) may still block the redirect. Manual fallback:

* Phantom → tap the compass / browser tab at the bottom → enter `snake-os.com`
* Solflare → menu → Browser → enter `snake-os.com`

Then connect normally inside the wallet's browser.

## After Connecting

The first time you connect:

1. Your wallet signs a one-time message — `"Snake OS - sign in"` — which proves you own the wallet. This signature is cached for one hour in your browser session. **No fee, no transaction.**
2. The app prompts you to accept the Terms of Service. See [Accepting the Terms](accepting-tos.md).
3. You land on the home screen with all 18 apps.

## Why We Sign a Message

The signature is how Snake OS knows the wallet you claim to own is actually yours. Without it, anyone could send API calls pretending to be you. The signed message:

* Is valid for 1 hour, then prompted again on the next sensitive action
* Costs zero SOL (signing ≠ transacting)
* Is verified server-side using ed25519 before any state change happens
* Is bound to the `snake-os.com` origin — clones serving our bundle can't impersonate you

## Disconnecting

Tap your wallet badge → DISCONNECT. This:

* Clears the cached signature from your browser
* Disconnects the wallet adapter
* Returns you to the connect screen

Your on-chain assets and Snake OS account data are untouched — disconnect only ends the current session.
