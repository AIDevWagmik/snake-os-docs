# FAQ & Troubleshooting

## General

**Is Snake OS available in my country?**
Open to anyone 18+ not in a comprehensively sanctioned jurisdiction (OFAC list). No IP geo-blocking — legal responsibility rests with you per the Terms.

**Can I have multiple accounts?**
One wallet = one account. Different wallets = different accounts. Wash-trading PvP between your own wallets is a bannable offense.

**What happens if I lose my seed phrase?**
Your Snake OS account is bound to your wallet address. If you lose the wallet, you lose access to the account and any claimable SOL balance. We can't recover it. Back up your seed phrase.

**Can I delete my account?**
No self-serve delete currently. Post-launch we'll add one. On-chain transaction history is public on Solana and can't be deleted by anyone.

**Is the source code open?**
Currently no. Post-launch we plan to open-source game logic and UI. Custodial escrow + admin tools stay closed (or move to audited on-chain programs).

---

## Wallet & Connection

**Wallet won't connect on mobile**

1. Make sure you're in Phantom's in-app browser (not Chrome/Safari directly)
2. On Android: open the site in Chrome first → tap CONNECT → you'll be redirected into Phantom's browser
3. On iOS: use the Phantom app's built-in browser
4. On Seeker: use the Solana Mobile dApp Store (MWA connects automatically)
5. Hard-refresh the page if the connect modal doesn't appear

**Can I use a hardware wallet?**
Phantom + Ledger on desktop works. Mobile flows don't support hardware wallets.

**"Origin not allowed" or 403 error**
You're either on a clone site or using a VPN/proxy that altered the Origin header. Make sure you're at exactly `https://snake-os.com`.

**Auth expired / "sign in again" prompt**
The auth signature is valid for 1 hour (15 min on money endpoints). Just sign again — it's free and takes one tap.

---

## PvP & Matches

**Match is stuck in "ready" state**
If your opponent goes offline after both depositing, the match auto-cancels in ~5 minutes and your deposit is refunded to your `claimable_pvp_sol` balance.

**I won but didn't get my SOL**
Winnings go to `claimable_pvp_sol` first — open REWARDS and claim from there. They don't arrive in your wallet automatically.

**Claim failed — try again**
The balance is restored atomically on failure, so retrying is safe. If it keeps failing: Solana may be congested, or the treasury balance is temporarily low. Wait 30–60 seconds and try again. If still failing after 5 minutes, report in Telegram with the timestamp.

**Refund didn't arrive**
Refunds go to `claimable_pvp_sol` (not directly on-chain). Open REWARDS and claim. If the REWARDS app shows no balance but you expected a refund, report in Telegram.

**"Nothing to claim" error**
Your `claimable_pvp_sol` balance is 0. If you just won a match, wait a few seconds for the settle to complete and refresh.

---

## BITS & Achievements

**BITS not showing up after an activity**
Most activities have daily caps. If you've hit the cap for that activity today, BITS won't be awarded until tomorrow. Check your balance in the REWARDS app.

**Achievement won't unlock**
Some achievements auto-unlock when the server detects the condition is met. If it's not showing: make sure you've met the full condition (e.g., Chat Regular requires 50 messages all time, not just today), then open the BADGES screen to trigger a refresh.

**BITS leaderboard claim failed**
Leaderboard BITS use a per-period cap key — one claim per wallet per week (SOLO/PVP) or per month (SEASON). If you already claimed this period, the button will confirm it was already collected.

---

## General Errors

**"Something went wrong" on any screen**
Hard-refresh (Ctrl+Shift+R / Cmd+Shift+R) usually fixes transient state issues.

**Images not loading (market items, PFPs)**
Some market item images are still being added. 404 images on cosmetics are expected during beta and don't affect functionality.

**Score not saving**
Score submission requires a signed wallet. If your auth expired mid-game, re-sign and the next game will save. In-flight game scores lost due to auth expiry can't be recovered.

---

## Contact

- **Telegram:** t.me/snakeOS_sol
- **X:** @SnakeOS_SOL
- **Email:** see [Contact](legal/contact.md)
