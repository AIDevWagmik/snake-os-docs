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

### Android shows only "Mobile Wallet Adapter" — no Phantom/Solflare buttons

That's intentional. MWA is the canonical Android path; it routes to Phantom, Solflare, or Backpack through the system wallet picker. Tap MWA → pick your wallet in the sheet.

## On Desktop

### Wallet extension not detected

1. Make sure the extension is installed and enabled
2. Refresh Snake OS
3. Try a different browser (Brave, Chrome, Firefox)
4. Check if the extension is on the correct network (Solana mainnet)

### Signature popup not appearing

1. Check your extension popup blocker — Phantom/Solflare popups can be silently blocked
2. Look in your wallet's pending request queue (some wallets queue requests instead of popping immediately)
