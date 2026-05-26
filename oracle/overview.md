# What ORACLE Does

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 142100.png" alt=""><figcaption></figcaption></figure>

ORACLE is Snake OS's built-in AI assistant + Solana token risk scanner. Two modes in one app:

## Mode 1: Token Risk Scan (Free + Unlimited)

Paste any Solana token contract address (CA) into the chat box → ORACLE returns a structured risk report:

* ✅/⚠/✗ **Verdict** (SAFE / CAUTION / RISKY / LIKELY RUG)
* **Risk score** (0–100)
* **Market cap**, **liquidity**, **24h volume**
* **Flags** — concrete warning signals (top-10 holder %, low liquidity, mint authority active, freeze authority active, etc.)
* All powered by trustfi + DexScreener data

**This path is UNMETERED.** Paste-CA scans are free and unlimited. No per-message cost.

## Mode 2: Free-Form Chat (Metered)

Ask ORACLE general questions — Solana ecosystem, memecoin trading concepts, Snake OS feature questions, perp commentary, token recommendations, anything not tied to a specific CA.

This path uses Gemini 2.5 Flash (with DeepSeek V3 fallback) and **does cost real AI tokens**, so it's rate-limited (see [Chat Limits](chat-limits.md) for full details).

### Engagement rewrite

ORACLE used to default to refusal-mode on directional questions ("I don't give recommendations" / "paste a CA"). It now actively engages on:

- **"What spot tokens should I buy?"** → names actual SOL ecosystem tokens with brief justification
- **"What perp to long/short?"** → reads the RADAR feed (if open) for grounded directional reads
- **"What's your read on [TOKEN]?"** → discusses the project / sector / liquidity tier even without a CA pasted, then asks for the CA for an on-chain scan
- **Sparse RADAR data** → falls back to general market-structure knowledge (BTC dominance, macro context, sector rotations) instead of refusing

Closes with a one-fragment disclaimer (`— speculative.`) on directional reads. Length capped at 3 sentences for any non-data answer — the model is on a phone screen, not a research note.

### Spam Protection

Burst-spam protection runs above the general rate limits:

- **4 messages in 8 seconds** trips a short cooldown with a friendly warning
- **6 cooldown trips in 10 minutes** flags the wallet (soft flag for ops review, not auto-ban)

Normal conversation pace doesn't trigger anything. Sustained rapid-fire from one wallet does. See [Chat Limits](chat-limits.md) for the full picture.

## RADAR Integration

When RADAR is open with fresh data (≤ 5 min old), ORACLE chat reads the live RADAR snapshot. Asking "what perp should I take" gets a directional answer grounded in the actual funding rates, OI surges, and whale flow — not generic market commentary.

If RADAR is closed or data is stale, ORACLE falls back to general knowledge with a caveat.

## When to Use Which

* "Is this CA a rug?" → paste the CA → instant scan (free)
* "What spot tokens to buy?" → free-chat (metered) — gets actual recommendations
* "What perp to take?" → open RADAR first, then ask → gets data-grounded read
* "What does 'mint authority' mean?" → free-chat (metered)
* "Thoughts on BONK?" → free-chat → ORACLE discusses the project, then asks for CA for on-chain scan
