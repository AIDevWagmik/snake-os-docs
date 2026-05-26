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

Ask ORACLE general questions — Solana ecosystem, memecoin trading concepts, Snake OS feature questions, anything not tied to a specific CA.

This path uses Gemini 2.5 Flash (with DeepSeek V3 fallback) and **does cost real AI tokens**, so it's rate-limited:

* **20 requests per minute** per IP (anti-burst)
* **40 messages per day per wallet** (personal cap)
* **2000 messages per day globally** (hard ceiling so IP-rotation abuse can't run the bill past \~$1-2/day)

These limits are cost-control, not monetization. Token scans stay free + unlimited even if you hit your chat cap.

## When to Use Which

* "Is this CA a rug?" → paste the CA → instant scan (free)
* "What does 'mint authority' mean?" → free-chat question (metered)
* "What do you think of XYZ memecoin's chart?" → free-chat question (ORACLE will redirect you to MARKET WATCH or risk-scan via CA paste)
