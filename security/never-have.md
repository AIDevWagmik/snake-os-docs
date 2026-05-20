# What We Never Have

A clarifying list of what Snake OS has zero access to:

## We NEVER Have

* ❌ Your wallet's **private key**
* ❌ Your **seed phrase**
* ❌ The ability to **spend your SOL** without your explicit approval
* ❌ The ability to **read your wallet activity** beyond what's on-chain (which is public anyway)
* ❌ Your **email address** (we don't collect emails)
* ❌ Your **phone number**
* ❌ Your **IP address linked to your wallet** in any persistent table (we rate-limit per IP at the edge but don't store the mapping)
* ❌ Your **real-world identity** (Snake OS is pseudonymous — wallet address is the only ID)
* ❌ A **back door** to your account

## We DO Have

* ✅ Your **wallet address** (public on Solana anyway)
* ✅ Your **gameplay data** (scores, matches, achievements)
* ✅ Your **on-chain TX signatures** from PvP deposits + market purchases (public on Solana)
* ✅ Your **selected username** (you chose it)
* ✅ Your **equipped cosmetics** (you chose them)
* ✅ Your **chat messages** (you posted them)
* ✅ **Aggregate IP rate-limiting counters** (transient, in-memory, not linked to wallet)
* ✅ **TOS acceptance timestamp + version**

If you delete your account post-launch (feature TBD), we delete everything except on-chain history (which is public and immutable on Solana).

## What This Means in Practice

* Worst-case scenario for our security: someone breaches our backend → they get gameplay data, not wallet keys
* We cannot "go rogue" and drain wallets — structurally impossible
* We cannot "be coerced" to drain wallets — we don't have the keys
* We cannot "accidentally leak" wallet keys — we don't have them
