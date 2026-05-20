# Other Common Questions

## Is Snake OS available in my country?

Snake OS is open to anyone 18+ NOT residing in or a citizen of a comprehensively sanctioned country (OFAC list). We don't do geo-blocking at the IP level — the legal responsibility for compliance rests with you per the Terms of Service.

## Can I use a hardware wallet?

If the wallet adapter supports it (Phantom + Ledger combo works), yes. Hardware wallets sign the same auth message + TXs as any other wallet. Note that mobile flows may not work — hardware wallets are typically desktop-only.

## Can I have multiple accounts?

One wallet = one account. Different wallets = different accounts. You can have multiple wallets, but:

* Each wallet has its own stats, friends, achievements
* Wash-trading PvP between your own wallets is a bannable offense per the Terms
* Beta slots are 1 per wallet — you can't claim slot 5 with one wallet and slot 11 with another to grab two BETA badges

## What happens to my account if I lose my seed phrase?

Your Snake OS account is bound to your wallet address. If you lose the wallet, you lose access to the account (we can't recover it — we don't have your keys). Any SOL in `claimable_pvp_sol` would also be inaccessible.

**Back up your seed phrase.** This is true of every Solana app.

## Can I delete my account?

Currently no self-serve delete. Post-launch we'll add a "delete account" option that wipes profile data (username, friends, chat history, achievements). On-chain TX history (deposits, payouts) is public on Solana and can't be deleted by anyone.

## Is the source code open?

Currently no — beta is closed-source while we iterate. Post-launch we plan to open-source non-critical parts (game logic, UI) for community credibility. Custodial escrow + admin tools stay closed (or eventually move to fully on-chain with audited Solana programs).

## How do I report a bug?

In-app HELP screen has a contact link, or post in our [Telegram support topic](https://t.me/snakeOS_sol). Include:

* What you tried to do
* What happened instead
* Screenshot if possible
* Browser + wallet
* Your wallet address (for log lookup)

## How do I report a security issue?

Report it in the support topic on Telegram with the word "security" in the message. We respond fast. Responsible disclosure = bug bounty rewards (we'll set the amount based on severity).

## Where's the Discord?

Snake OS doesn't have a Discord yet. We may launch one post-token. For now, the community lives on [Telegram](https://t.me/snakeOS_sol) (with a dedicated support topic) and on X.
