# The SOCIALS App (Link Hub)

SOCIALS is the in-app link hub that mirrors **snake-os.com/links**. It surfaces every official Snake OS channel as a tappable row so users don't have to leave the phone to find them.

## What's in the hub

- 🌐 **Website** — snake-os.com
- 🐦 **X (Twitter)** — [@SnakeOS_SOL](https://x.com/SnakeOS_SOL)
- 💬 **Telegram** — [t.me/snakeOS_sol](https://t.me/snakeOS_sol)
- 👻 **Phantom dApp Portal** — phantom.com/apps/snakeos
- 📱 **Solana Mobile dApp Store** — for Seeker / Saga users
- 🎵 **TikTok** — [@snake.os](https://tiktok.com/@snake.os)
- 📚 **Docs** — docs.snake-os.com (you're reading them)
- 💻 **GitHub** — for development progress + commit transparency

Each row → tap → opens that destination in a new tab (`window.open`).

## Why SOCIALS exists in-app

Users open Snake OS to play and trade. When they want to follow the project externally — join the Telegram for support, follow the X for launch updates, install on Seeker — the friction of leaving the phone to find a links page is real. SOCIALS keeps those one tap away.

Also: the dApp Store version (TWA) of Snake OS doesn't have the browser address bar. SOCIALS is how users discover those external channels without typing a URL.

## Same data, two surfaces

The link set in SOCIALS is the same data that powers **snake-os.com/links** (Snake OS's self-hosted Linktree replacement). One source of truth (`SOCIAL_LINKS` in code), two consumers:

- The in-app SOCIALS screen
- The public `/links` page

When Snake OS adds a new official channel (e.g. Discord launch, Instagram account), it ships in both places at once.

## Why not Linktree

Snake OS got banned from Linktree for being "gambling-related" (we're not — PvP is skill-based on-chain, not a casino). Rather than fight a misclassification, we self-hosted `/links` and rebuilt the same UX in-app as SOCIALS. Now we control the surface entirely and no third party can yank it.

See snake-os.com/links for the public-facing equivalent.

## What SOCIALS is not

- **Not a friends list.** For social connections inside Snake OS, see [Friends](friends.md).
- **Not a chat surface.** Snake OS's internal chat lives in [Global Chat](chat.md).
- **Not editable by users.** The link set is curated and shipped with deploys.
