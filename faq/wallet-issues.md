# Wallet Won't Connect

## On Mobile

### Phantom in-app browser keypad clipped

Fixed in current build. Phone scales to `min(100vw, 47dvh)` so all 9 keys are visible. If you still see clipping, force-refresh (pull down to reload) — you might be on a stale cache.

### Phantom in-app browser direct URL has limited space

The Phantom in-app browser has a bottom banner that eats viewport. Try this flow instead:

1. Open mobile Safari/Chrome
2. Go to snake-os.com
3. Tap CONNECT → choose Phantom → universal-link into Phantom app
4. Approve there → return to browser
5. Now Phantom's bottom banner dismisses and the full keypad fits

### Android wallet button doesn't open Phantom

Tap the Phantom button → you should be auto-redirected into Phantom's in-app browser with snake-os.com pre-loaded. If nothing happens after 2 seconds:

* You may be on a browser that blocks all universal-link redirects (Samsung Internet, older Chrome)
* Or the Phantom app isn't installed on this device

**Manual fallback (always works):** open snake-os.com directly inside Phantom's built-in browser:

* Phantom → bottom compass / browser icon → enter `snake-os.com`

Connect from there. Once you're inside Phantom's browser, the connect handshake runs normally and is identical to desktop.

### MWA on Seeker doesn't fire

If you're running Snake OS inside the Solana Mobile dApp Store app on Seeker and the MWA prompt doesn't appear:

1. Confirm you're using the dApp Store app, not the regular Chrome
2. Make sure Seed Vault (or another MWA-compatible wallet) is installed and unlocked
3. Try closing and reopening the Snake OS app
4. If still stuck, force-stop the app from Android settings and relaunch

MWA only works inside the Solana Mobile dApp Store environment — regular Android Chrome falls back to Phantom.

## On Desktop

### Wallet extension not detected

1. Make sure the Phantom extension is installed and enabled
2. Refresh Snake OS
3. Try a different browser (Brave, Chrome, Firefox)
4. Check if the extension is on the correct network (Solana mainnet)

### Signature popup not appearing

1. Check your extension popup blocker — Phantom popups can be silently blocked
2. Look in your wallet's pending request queue (Phantom occasionally queues requests instead of popping immediately)

### Wallet I prefer isn't listed

We officially support **Phantom + MWA** only. Solflare and Backpack were removed during beta due to adapter reliability issues. See [Connecting Your Wallet → Why Phantom Only?](../getting-started/connecting-wallet.md#why-phantom-only) for the reasoning.
