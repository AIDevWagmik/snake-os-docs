# Wallet Won't Connect

## On Mobile

### Solflare in-app browser shows the keypad clipped

Fixed in current build. Phone scales to `min(100vw, 47dvh)` so all 9 keys are visible on every tested wallet browser. If you still see clipping, force-refresh (pull down to reload) — you might be on a stale cache.

### Phantom in-app browser direct URL has limited space

The Phantom in-app browser has a bottom banner that eats viewport. Try this flow instead:

1. Open mobile Safari/Chrome
2. Go to snake-os.com
3. Tap CONNECT → choose Phantom → universal-link into Phantom app
4. Approve there → return to browser
5. Now Phantom's bottom banner dismisses and the full keypad fits

### Android wallet button doesn't open the wallet

Tap the wallet button → you should be auto-redirected into the wallet's in-app browser with snake-os.com pre-loaded. If nothing happens after 2 seconds:

* You may be on a browser that blocks all universal-link redirects (Samsung Internet, older Chrome)
* Or the wallet app isn't installed on this device

**Manual fallback (always works):** open snake-os.com directly inside the wallet's built-in browser:

* Phantom → bottom compass / browser icon → enter `snake-os.com`
* Solflare → menu → Browser → enter `snake-os.com`
* Backpack → browser tab → enter `snake-os.com`

Connect from there. Once you're inside the wallet's browser, the connect handshake runs normally and is identical to desktop.

## On Desktop

### Wallet extension not detected

1. Make sure the extension is installed and enabled
2. Refresh Snake OS
3. Try a different browser (Brave, Chrome, Firefox)
4. Check if the extension is on the correct network (Solana mainnet)

### Signature popup not appearing

1. Check your extension popup blocker — Phantom/Solflare popups can be silently blocked
2. Look in your wallet's pending request queue (some wallets queue requests instead of popping immediately)
