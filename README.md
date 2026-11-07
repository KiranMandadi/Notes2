Two layout changes. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Pending Quality column: stack the score above the status pill.
   - Line 1: the score as a plain number, 14 px, semibold, #1C2A42. No "/100" and no status colour on the number.
   - Line 2: the existing status pill, slightly smaller (11 px text, 2 px × 8 px padding).
   - Left-aligned, 4 px gap. While scores load, the existing "Checking…" placeholder takes the place of both lines.
   - Narrow the Quality column from about 150 px to about 96 px and give the space to the Change column.
   - Add the tooltip "Quality score out of 100" on the QUALITY column header.
   - Same order in the phone cards. Sorting by Quality is unchanged.

2. Page width.
   - Pending, Review and Rules: content max-width 1600 px (from 1280), centred, with a 32 px side margin (24 px below 1440 px wide).
   - The dark header uses the same max-width and side margin, so the logo, title and buttons line up with the content edges.
   - Pending: the extra width goes to the Change column only; the other columns keep their fixed widths.
   - Quality report (standalone and in the overlay) and the Executive brief: content max-width about 1360 px, for readability.
   - Phone layout unchanged. Check that nothing is wider than the window at 1280, 1440 and 1920 px, and that Window's lines still don't wrap.

3. Tests and docs: the stacked Quality cell (score, pill, Checking state, header tooltip, column width); max-widths per page at 1280, 1440 and 1920 px with no horizontal scroll; the header aligned with the content. Update the user guide screenshots and CHANGELOG (no new version). Run the browser tests and `python scripts/check.py --browser --audit`; report counts. Screenshots to work/preview/ at 1440 and 1920 px.

No branches, tags or commits.

git status
git add -A
git commit -m "Pending: stacked Quality column; wider page layout (1600 px lists, 1360 px report)"
git push