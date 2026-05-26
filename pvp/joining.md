# Joining a Match

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 141152.png" alt=""><figcaption></figcaption></figure>

## Step-by-Step

1. Open **PVP** app → lobby tab.
2. Browse waiting matches — each shows the creator's username and wager.
3. Tap a match → tap **JOIN**.
4. Approve the on-chain deposit transaction in your wallet.
   * You're depositing the SAME wager amount as the creator
   * SOL goes to the treasury, sig recorded as `p2_deposit_sig`
5. Match status flips to `ready`.
6. Tap **READY** when you're prepared to play.
7. When both players have tapped READY, the game starts simultaneously for both.

## CAS Slot Protection

If two players try to JOIN the same `waiting` match at the same time, only one wins (the CAS guard ensures only one DB update succeeds). The other gets a "match no longer available" error and their wallet doesn't get debited — the deposit only fires after the JOIN succeeds.

## Match Discovery

The lobby polls every \~20 seconds for new matches. You can also accept a **direct PvP invite** from a friend — see [Notifications](../social/notifications.md). Direct invites bypass the lobby.

## What If I Join Then Drop?

* If you joined but didn't deposit → no SOL moved, no harm.
* If you joined + deposited but never readied → the match sits in `ready` until either you or the opponent cancels (refund follows). Currently no auto-cancel for stuck `ready` matches — post in our [Telegram support topic](https://t.me/snakeOS_sol) if this happens.
* If both readied + the game starts + you disconnect mid-game → your score may be 0, opponent wins by default. Refunds don't apply once `playing` starts.
