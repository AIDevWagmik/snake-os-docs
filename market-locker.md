# Market, Locker & History

## 🛒 Market

The cosmetics marketplace. Buy skins, arenas, themes, PFPs, badges, and bundles with SOL.

### Purchase flow

1. Open MARKET → browse items
2. Tap an item → see price + preview
3. Tap BUY → wallet prompts for a SOL transfer to the treasury wallet
4. Server verifies the deposit on-chain (amount, destination, signature uniqueness)
5. Item is permanently added to your Locker

**Replay protection** — each deposit signature can only be used once. Duplicate sigs are rejected (409).

**Server-side prices** — the server holds the authoritative price table. Client-supplied prices are ignored.

DEV_WALLET (OG beta) and beta-badge wallets receive all market items free for the pre-launch period. Dev wallet still pays real SOL for PvP matches.

---

## 🎒 Locker

Equip cosmetics you own. Categories:

| Slot | Options |
|------|---------|
| Skin | Snake body color + style |
| Arena | Game background |
| Theme | Phone UI color scheme |
| PFP | Profile picture (avatar shown in chat + friends + leaderboard) |
| Badge | Displayed next to your username everywhere |

Tap any owned item → EQUIP. Changes take effect immediately across chat, leaderboard, and friends list.

**Free starter items** (all new accounts):
- Skins: CLASSIC GREEN, TOXIC, SHADOW, LAVA SNAKE, SOL VIPER
- Arenas: CLASSIC GRID, JUNGLE RUINS
- Themes: CLASSIC GREEN, MATRIX, CYBER, PEPE, WIF

---

## 🏅 BETA Badge

The first 20 wallets to accept Terms of Service get a permanent **BETA** badge. It displays next to your username in chat, friends list, and leaderboard — forever. It can never be earned again after the 20 slots are filled.

Market badge items are also equippable (4 purchasable badge types). Only one badge is worn at a time.

---

## 📜 History

Full log of your past Snake matches — solo, PvP, challenge, and tournament. Shows:
- Date and mode
- Score achieved
- Opponent (PvP)
- Wager and outcome (PvP/challenge)

History is read-only. Useful for tracking your improvement or verifying a payout dispute.
