# Rematches

## How They Work

After a match settles, either player can offer a **rematch** to the same opponent.

1. Tap **REMATCH** on the post-match screen.
2. A new `pvp_matches` row is created with `rematch_of_id` pointing to the original.
3. A `rematch_invite` notification is dropped to your opponent.
4. They have 10 seconds to ACCEPT (the notification polls every 10s).
5. If they accept → new lobby flow starts (deposit → ready → play).
6. If they decline or timeout → the new match auto-cancels.

## Wager Inheritance

Rematches inherit the previous match's wager amount by default. You can change it in the offer screen (still subject to 0.01–10 SOL bounds).

## Why Rematches?

The classic gambler dynamic: "double or nothing." But also the legitimate desire to play a longer set against a worthy opponent — best-of-3, best-of-5, etc. Rematches make extended skill duels possible without going back to the lobby every match.
