Two overlay fixes. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Lock the Pending page while the overlay is open, and restore it exactly on close.
   - On open, save window.scrollY (and the calendar's scroll position if it has one). Lock the page: html/body overflow hidden, with scrollbar-gutter: stable (or padding equal to the scrollbar width) so nothing shifts sideways. No scroll chaining: overscroll-behavior: contain on the overlay and its embedded report, and wheel/touch events on the backdrop strip must not scroll the page.
   - While open, never scroll the Pending page: stepping must not scrollIntoView the list, and the sticky compact header must not toggle.
   - On close (Esc, ×, Back to Pending, the strip, or browser Back): unlock, restore the exact saved position, then return focus to the row's "Open →" with focus({ preventScroll: true }). Keep the row highlight. If that row is off screen, leave it; don't scroll to it.
   - Set history.scrollRestoration = "manual" on Pending so ?open= history entries don't make the browser move the page.
   - Filters, tab, sort, layout and calendar week stay as they are (already required).
   - Tests: scroll Pending to the middle, open a change, wheel over the strip, step › five times, close by each method (Esc, ×, Back to Pending, the strip, browser Back), and assert scrollY is identical (±0 px) and nothing shifted sideways. Same for the calendar layout and at 390 px.

2. Backdrop: a medium dim instead of near-white. rgba(11,27,51,0.28) with backdrop-filter: blur(2px), falling back to rgba(11,27,51,0.34) without blur. Keep the overlay's 1 px #CFD7E3 border, shadow, light toolbar, and the 72 px strip that closes it. Update the backdrop colour test.

Update the 0.45.0 CHANGELOG and decisions lines (no new version). Run the browser tests and `python scripts/check.py --browser --audit`; report counts. No branches, tags or commits.

git status
git add -A
git commit -m "Overlay: lock Pending scroll and restore it exactly on close; medium dim backdrop (0.45.0)"
git push