# Connecting Your Wallet

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 104010.png" alt=""><figcaption></figcaption></figure>

Snake OS supports three wallet paths:

## Desktop / Laptop

| Wallet      | How                                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------------- |
| **Phantom** | Install [Phantom](https://phantom.app) browser extension → click CONNECT on Snake OS → approve in popup |

## iOS

| Wallet              | How                                                                                                                                             |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Phantom**         | Open Safari → snake-os.com → tap CONNECT → choose Phantom → confirm in Phantom app (universal link)                                             |
| **In-app browsers** | Open Phantom app → tap the browser tab at the bottom → enter `snake-os.com` → CONNECT → approve. Works the same way, just stays inside Phantom. |

## Android

The wallet picker changes depending on where you're using Snake OS from:

#### Inside the Solana Mobile dApp Store app (Seeker)



You'll see **Mobile Wallet Adapter (MWA)** as the connection option. Tap CONNECT → Android shows the system wallet picker → choose **Seed Vault** (or another MWA-compatible wallet you have installed) → biometric / PIN approval → connected.

This is the most secure path on Seeker — MWA handles the secure key exchange between Snake OS and your wallet without exposing keys to the browser.

### Inside regular Android Chrome (or Samsung Internet, Brave, etc.)

You'll see **Phantom** as the connection option. MWA is hidden here because Android Chrome can't reliably route MWA intents to wallet apps (the prompt fires but Seed Vault never opens consistently).

The flow on regular Chrome:

1. Open Chrome → snake-os.com → tap **CONNECT**
2. Pick **Phantom**
3. You'll be redirected into the Phantom app, with snake-os.com pre-loaded inside its built-in browser
4. Inside Phantom's browser, tap **CONNECT** again → approve
5. Done

One extra tap vs. iOS, but reliable on every Android browser we've tested.

> **Seeker users in plain Chrome:** install the Snake OS dApp Store app for the native MWA → Seed Vault flow. From regular Chrome you can still use Phantom if you have it installed — just one extra tap.

### If the redirect doesn't fire

Some Android browsers (Samsung Internet, older Chrome versions) may still block the redirect. Manual fallback:

* Phantom → tap the compass / browser tab at the bottom → enter `snake-os.com`

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
