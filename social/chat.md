# Global Chat

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142448.png" alt=""><figcaption></figcaption></figure>

The CHAT app is a single global feed visible to all Snake OS users. Open with key **8** or the CHAT home icon.

## What You See

Each message shows:

* Sender's PFP (or fallback avatar)
* Username
* **BETA badge** (if sender is a closed-beta OG)
* **Equipped badge** (their currently-worn market badge)
* Timestamp
* Message body
* Type tag (GLOBAL / TAUNT / CHAT)

## Sending Messages

* 200-character limit per message
* Quick-emote palette (12 common emotes)
* Quick-msg palette (predefined common messages)
* Or type freely

## Rate Limits

* **30 messages per minute** per wallet
* Type whitelist enforced server-side (only `global`, `chat`, `taunt` accepted — no system/admin impersonation possible)
* Banned users (`is_banned=true`) blocked from posting

## Why a Single Global Feed?

We deliberately kept chat simple during beta — one global room, no DMs, no rooms/channels. Easier to moderate, easier for new users to immediately see other players, builds community fast. DMs + topic rooms may come post-launch.

## Optimistic Insert

When you send a message, it appears in your client immediately (optimistic insert) before the server confirms. If the send fails, the optimistic message stays visible until the next poll, then drops if not confirmed by the server.
