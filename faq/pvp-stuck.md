# PvP Match Stuck

## My match shows "waiting" forever

If 5 minutes have passed and no opponent joined:

* The lobby sweep should auto-cancel within the next poll cycle
* You'll get a notification + on-chain refund within ~30 seconds of the 5-minute mark
* If 10+ minutes have passed without notification, please report it in the support topic on Telegram with the match ID

## I deposited, opponent joined + deposited, but the game never started

Match is in `ready` state but neither of you tapped READY. The game only starts when BOTH have clicked READY.

* Both players tap **READY** to start
* If your opponent disappears: currently no auto-cancel for stuck `ready` matches. Report it in the support topic on Telegram with the match ID and we'll manually cancel + refund both sides.

## Game ended but score didn't submit

The score submission has built-in retry. If it fails:

1. Don't refresh — the local score is held in memory
2. Wait 5 seconds, the retry fires
3. If still failing, check your network connection
4. Report it in the support topic on Telegram with a screenshot of the final score + match ID

## I won but didn't get my claim

1. Open REWARDS app → check `claimable_pvp_sol` balance
2. If the balance shows your winnings, tap CLAIM
3. If the balance is 0 but you won: the settle may not have processed yet (eventual consistency, ~30 sec)
4. If 5+ minutes pass and balance still 0, please report it in the support topic on Telegram with the match ID
