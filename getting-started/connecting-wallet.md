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

On Android, you'll see **one** "Mobile Wallet Adapter" button (we collapse the wallet picker to MWA because the bare adapters can't reliably deep-link from Android browsers).

1. Tap **Mobile Wallet Adapter** → CONNECT
2. Android opens a wallet picker sheet
3. Choose Phantom, Solflare, or Backpack
4. Approve the connection in the wallet app
5. You're returned to Snake OS, signed in

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
