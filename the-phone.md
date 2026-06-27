# The Phone

## Layout

Snake OS is rendered as a Nokia 3310, top to bottom:

| Region | What |
|--------|------|
| Header | NOKIA logo + signal/clock |
| LCD Screen | Active app — 18 different screens |
| D-Pad | Navigation + snake movement |
| Softkeys | BACK (left) · END/power (right) |
| Number keys 1–9 | App shortcuts |
| Decorative row (`*`, `0`, `#`) | Visual only — not interactive |

On mobile the phone scales to `min(100vw, 47dvh)` so all 9 number keys stay visible with tap room. Row 4 is decorative and fully clipped.

---

## Controls

**D-Pad**

| Context | Action |
|---------|--------|
| Snake game | Turn the snake (up / down / left / right) |
| Other apps | Scroll content, navigate tabs |
| Center OK | Confirm / pause |
| Home screen | Move between app icons |

**Softkeys**

| Button | Action |
|--------|--------|
| ↩ BACK | Return to home from any app |
| ⏻ END | Power off (returns to boot screen) |

**Keyboard (desktop)**

Arrow keys control the snake and scroll apps — they're `preventDefault`'d so they never scroll the browser page. Enter = OK. Backspace = BACK.

---

## Number Key Shortcuts

| Key | App |
|-----|-----|
| 1 | SNAKE |
| 2 | LEADERBOARD |
| 3 | CHAT |
| 4 | REWARDS |
| 5 | HOME |
| 6 | DEGEN |
| 7 | MARKET WATCH |
| 8 | CHAT |
| 9 | LOCKER |

PVP and HISTORY are accessible only from home-screen icons (no key shortcut by design — prevents accidental entry into wagering screens).

---

## All Apps

| App | Purpose |
|-----|---------|
| 🐍 SNAKE | Classic snake — solo, challenge, tournament |
| ⚔ PVP | Real-SOL 1v1 match lobby |
| 🏆 LEADERBOARD | Global rankings |
| ★ REWARDS | PvP claims + BITS balance |
| 💼 WALLET | Connected wallet view (balance, activity) |
| 💸 BUY | Jupiter swap for any SPL token |
| 🛒 MARKET | Cosmetics marketplace |
| 🎒 LOCKER | Equip purchased cosmetics |
| 🏅 BADGES | Achievement list + progress |
| 📈 MARKET WATCH | Live charts — SOL, BTC, ETH + memes |
| 📡 RADAR | Perp signals — Hyperliquid + Phoenix |
| 🔮 ORACLE | AI risk scanner + chat for any Solana token |
| 🔥 DEGEN | pump.fun migrations + trending + boosted |
| 🎯 SNIPE | KOL wallet activity tracker |
| 🐦 CT FEED | Curated X posts from Solana KOLs |
| 💬 COMMUNITIES | Per-token discussion threads |
| 📈 STOCKS | 130+ tokenized real-world equities |
| 🤣 MEMES | Vertical-scroll curated meme feed |
| 👥 FRIENDS | Friend list + online presence |
| ✉ CHAT | Global Snake OS chat |
| 📜 HISTORY | Past match log |
| ⚙ SETTINGS | Username + preferences |

> **Notification badges** appear on PVP (pending invites), CHAT (unread), FRIENDS (incoming requests), REWARDS (claimable balance), and RADAR (new whale events).
