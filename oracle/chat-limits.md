# Free-Chat Limits

## Why There Are Limits

Free-form chat with ORACLE uses real AI provider tokens (Gemini 2.5 Flash, with DeepSeek V3 fallback). Each message costs ~$0.0003 in API calls. Without limits, a single abusive user could rack up $50+/day in costs.

## The Limits

| Limit | Value | Scope |
|---|---|---|
| Rate limit | 20 req/min | Per IP |
| Daily cap | 40 messages | Per wallet |
| Global cap | 2000 messages | All users combined |

## What Happens at the Limits

| Situation | What you see |
|---|---|
| IP rate-limited (>20/min) | "Slow down — too many requests" |
| Hit your daily 40 | "You've used today's 40 free Oracle chat messages. Resets in ~Xh. Token risk scans are still free + unlimited — just paste any contract address." |
| Global cap hit | "The Oracle is at capacity for today — high demand. Try again later. Token risk scans are still free — paste any contract address." |

## CA Scans Are Always Free

The 40/day cap **only** applies to free-chat. Pasting a contract address bypasses the AI providers entirely and runs on our own infra (trustfi + DexScreener). Scan as many tokens as you want — there's no cap.

## When ORACLE Is Offline

If both Gemini and DeepSeek fail:

> "⚠ Oracle is offline right now. Paste a Solana CA and I can still scan it via trustfi — that path doesn't need AI."

The CA-scan path stays alive even when the chat path is down.
