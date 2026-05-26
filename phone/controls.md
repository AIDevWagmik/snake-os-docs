# Navigation & Controls

<figure><img src="../.gitbook/assets/Screenshot 2026-05-26 140817.png" alt=""><figcaption></figcaption></figure>

## D-Pad

Four directional arrows + center **OK** button.

| Use            | What it does                                         |
| -------------- | ---------------------------------------------------- |
| In Snake game  | Turn the snake (up/down/left/right)                  |
| In other apps  | Scroll content (up/down), navigate tabs (left/right) |
| Center OK      | Confirm / select / pause                             |
| On home screen | Move focus between app icons                         |

## Softkeys

| Button     | What                                                                        |
| ---------- | --------------------------------------------------------------------------- |
| **↩ BACK** | Return to home screen from any app                                          |
| **⏻ END**  | Power off the phone (returns to boot screen — useful for switching wallets) |

## Quick Tips

* **Reaching for BACK doesn't accidentally hit the left arrow** — we added a 6px gap between the BACK softkey and the d-pad to prevent thumb-clip misfires.
* **Mobile fallback** — A floating ▤ HOME button appears top-left when not on home, in case the keypad is partially clipped on tight viewports.
* **Desktop keyboard** — Arrow keys, number keys 1-9, and Enter all work natively. Arrow keys are `preventDefault`'d so they don't scroll the page.

## Anti-Glitch Touch Handling

The keypad area uses `touch-action: none` across the entire subtree (container + gaps + buttons). This prevents iOS / Chrome from interpreting an imprecise rapid d-pad tap as a page-pan gesture, which would otherwise rubber-band the phone shell out of the screen frame. If you're on iOS and notice the page feels "locked" while tapping the keypad — that's intentional, in-app scrolling still works in any list / chat / market.

## Long-Press Suppression (Snake Game)

During snake gameplay, holding a d-pad arrow used to trigger iOS Safari's / Android Chrome's callout menu ("Save image" / selection handles), which froze touch input for ~0.5-1.5s — the snake would keep moving but you couldn't turn, dying mid-press.

The d-pad buttons and in-game overlay glyphs now suppress:
- `-webkit-touch-callout` (iOS save-image menu)
- `-webkit-user-select` / `user-select` (text selection start)
- `-webkit-user-drag` (drag-to-copy)
- `-webkit-tap-highlight-color` (the gray flash that delays tap response)

Result: long-press during gameplay does nothing visible, doesn't lock input, doesn't kill the snake.

## In-Game D-Pad Overlay

When snake is running, a neon-outlined overlay appears over the d-pad showing the four arrow hit zones + a center pause button. The hit zones use generous tap areas (50% wide × 32% tall for up/down, 32% × 50% for left/right) so imprecise thumb taps still register correctly. The center button shows `⏸` while playing and `▶` when paused.
