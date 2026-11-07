Overlay: solid backdrop and scroll lock. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Backdrop: replace the translucent scrim with a solid, opaque #2F3540 (no transparency, no blur), so the Pending page, including its header, is completely hidden while the overlay is open.
   - The overlay sits 24 px from all four edges (remove the 72 px left strip); full screen on phone, unchanged.
   - Keep its 16 px radius and 1 px #CFD7E3 border; use a shadow of 0 24px 64px rgba(0,0,0,0.35).
   - A click anywhere on the grey backdrop closes the overlay (tooltip "Back to Pending"). Keep the light toolbar.

2. Lock the Pending page while the overlay is open, and restore it exactly on close.
   - On open, save window.scrollY (and the calendar's scroll position if it has one), then lock the page: html/body overflow hidden, with scrollbar-gutter: stable (or padding equal to the scrollbar width) so nothing shifts sideways.
   - Use overscroll-behavior: contain on the overlay and the embedded report; wheel and touch on the backdrop must not scroll the page.
   - While open, never scroll Pending: stepping must not scrollIntoView the list, and the compact sticky header must not toggle.
   - On close (Esc, ×, Back to Pending, a backdrop click, or browser Back): unlock, restore the exact saved position, and return focus to the row's "Open →" with focus({ preventScroll: true }). Keep the row highlight, and don't scroll to the row if it's off screen.
   - Set history.scrollRestoration = "manual" on Pending.

3. Tests:
   - The backdrop is opaque #2F3540 and no part of Pending is visible.
   - The 24 px margins; a backdrop click closes the overlay.
   - Scroll Pending to the middle, open a change, wheel over the backdrop, step › five times, then close by each method: scrollY is identical (±0 px) with no sideways shift. Repeat in the calendar layout and at 390 px.

Update the 0.45.0 CHANGELOG and decisions lines (no new version). Run the browser tests and `python scripts/check.py --browser --audit`; report counts. No branches, tags or commits.