Layout and Review Decision placement. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Pending Quality column: stack the score above the status pill.
   - Line 1: the score as a plain number, 14 px, semibold, #1C2A42. No "/100" and no status colour on the number.
   - Line 2: the existing status pill, slightly smaller (11 px text, 2 px × 8 px padding).
   - Left-aligned with a 4 px gap. While scores load, the existing "Checking…" placeholder takes the place of both lines.
   - Narrow the Quality column from about 150 px to about 96 px and give the space to the Change column.
   - Add the tooltip "Quality score out of 100" on the QUALITY column header.
   - Same order in the phone cards; sorting by Quality is unchanged.

2. One page width everywhere: use the Quality report's current content width (about 1360 px max, centred, same side margins) for Review, Pending, Rules, the Quality report and the Executive brief.
   - Define it once, as a single shared CSS variable or class, and remove any page-specific widths, including the 1600 px change if it was applied.
   - The dark header uses the same width and margins, so the logo, title, nav and buttons line up with the content on every page.
   - Pending: the Change column stays the only flexible column.
   - Phone layout unchanged. No horizontal scroll at 1280, 1440 or 1920 px, and Window's lines still don't wrap at 1440 px.

3. Review Decision only in the overlay.
   - Show the Review Decision control (Approve / Needs work) and its A/N keyboard shortcuts only when the report is shown in the overlay's embedded mode.
   - Hide them on the standalone report: opened from Review search, a direct link, or Ctrl/⌘-click from Pending.
   - Decisions already made stay in the tab and keep showing on Pending.
   - Remove any now-unused standalone-only decision code.

4. Tests:
   - the stacked Quality cell (score, pill, Checking state, header tooltip, column width);
   - the same content width and header alignment on all five pages at 1280, 1440 and 1920 px;
   - the decision control present and the A/N keys working in the overlay;
   - the control absent and the A/N keys inert on the standalone report (from Review search and from a direct link).
   Update the user guide, decisions.md and CHANGELOG (no new version). Run the browser tests and `python scripts/check.py --browser --audit`; report counts. Screenshots to work/preview/ at 1440 and 1920 px.

No branches, tags or commits.

git status
git add -A
git commit -m "One page width across the Console; stacked Quality column; Review Decision only in the Pending overlay"
git push