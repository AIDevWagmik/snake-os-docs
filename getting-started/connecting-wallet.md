# Connecting Your Wallet

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 104010.png" alt=""><figcaption></figcaption></figure>

Snake OS supports three wallet paths:

## Desktop / Laptop

| Wallet       | How                                                                                                               |
| ------------ | ----------------------------------------------------------------------------------------------------------------- |
| **Phantom**  | Install [Phantom](https://phantom.app) browser extension → click CONNECT on Snake OS → approve in popup           |
| **Solflare** | Install [Solflare](https://solflare.com) extension → CONNECT → approve                                            |
| **Backpack** | Install [Backpack](https://backpack.app) → CONNECT → approve. Backpack will appear as a Phantom-compatible option |

## iOS

| Wallet              | How                                                                                                       |
| ------------------- | --------------------------------------------------------------------------------------------------------- |
| **Phantom**         | Open Safari → snake-os.com → tap CONNECT → choose Phantom → confirm in Phantom app (universal link)       |
| **Solflare**        | Same flow via Solflare app                                                                                |
| **In-app browsers** | You can also open snake-os.com directly inside Phantom or Solflare's built-in browser. Works the same way |

## Android

The wallet picker changes depending on where you're using Snake OS from:

### Inside the Snake OS dApp Store app (Solana Mobile Seeker)

You'll see **Mobile Wallet Adapter** as the first option. Tap it → Android shows the system wallet picker → choose **Seed Vault** (or Phantom / Solflare if installed) → biometric / PIN approval → connected. This is the most secure path on Seeker.

### Inside regular Android Chrome (or Samsung Internet, Brave, etc.)

You'll see **Phantom**, **Solflare**, and **Backpack** in the picker. We don't offer MWA here — Android Chrome can't reliably route MWA intents to wallet apps (the prompt fires but Seed Vault never opens). Instead the bare wallet buttons auto-redirect you into the wallet's own in-app browser:

1. Open Chrome → snake-os.com → tap **CONNECT**
2. Pick **Phantom**, **Solflare**, or **Backpack**
3. You'll be redirected into the wallet's app, with snake-os.com pre-loaded inside its built-in browser
4. Inside the wallet's browser, tap **CONNECT** again → approve
5. Done

One extra tap vs. iOS, but reliable on every Android browser we've tested.

> **Seeker users in plain Chrome:** install the Snake OS dApp Store app for the native MWA → Seed Vault flow. From regular Chrome you can still use Phantom or Solflare if you have those installed.

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
