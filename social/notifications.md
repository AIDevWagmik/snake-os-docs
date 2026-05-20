# Notifications

In-app notifications surface time-sensitive events.

## Notification Types

| Type | Triggers |
|---|---|
| `pvp_invite` | Friend sent you a direct PvP match invite |
| `rematch_invite` | Opponent offered a rematch after settle |
| `match_settled` | A match you're in just settled (winner/loser notified) |
| `wallet` | Wallet event (refund processed, payout sent) |
| `friend_request` | Someone sent you a friend request |
| `friend_accepted` | Someone accepted your friend request |
| `system` | Admin announcements |

## Where They Appear

* A bell/badge appears on the home screen with unread count
* Tap to open the notification panel
* Each notification shows sender / event + action buttons (JOIN, ACCEPT, DECLINE, DISMISS)

## Polling

Notifications poll every ~20 seconds. Time-critical ones (PvP invites with 10-second windows) have shorter polls during the active window.

## Dismissing

* Tap **PASS** / **DECLINE** / **DISMISS** depending on type
* Dismissed notifications are marked read server-side and won't reappear
* They stay archived in your notification history (last 50)
