Polish on the executive Pending page (0.41.0). Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never run crq login; live data only; codes and counts only in replies.

1. Search box: 20% narrower than now. It must always show the placeholder text "CRQ, summary or product" next to the magnifier icon (drop only the word "Search"). The full placeholder must be visible, not truncated, at 1440 and 1280 px; if 20% narrower would cut it off, make it only as narrow as the full text allows. Accessible label: aria-label="Search CRQ, summary or product". The view card must stay on one row at 1440 px, and at 1280 px with 3-digit counts.

2. Window column: the duration and all its tags (Today/Tomorrow, Freeze, Freeze · exception) stay on one line at 1440 px. Make the Change column 5% narrower to give Window the room; the date line and the duration+tags line never wrap at 1440 px. Below 1280 px, tags may wrap as a group under the duration.

3. Sort icons: every sortable header (Change, Window, Risk, Quality) shows a neutral ↕ icon in muted grey. The active column shows a solid ↑ or ↓ with its header text in the active colour (as Risk ↓ looks now). Quality's icon is dimmed and the header not clickable until all scores arrive (tooltip as before). # and Report have no icon.

4. Today vs Tomorrow: "Today" becomes solid blue (#1E40AF background, white text); "Tomorrow" keeps the pale blue (#E0ECFF / #1E40AF). Same in the phone cards and the PDF.

5. PRODUCT line: one line, truncated with an ellipsis; the full product name in a tooltip (title). Same rule in the PDF, but wrapping is allowed there.

6. Sticky table header: the column header row (with sort icons) stays visible while scrolling the table on desktop; not in the PDF or the phone card layout.

Update browser/screen tests and screenshots in work/preview/ (1440, 1280, 1024, 760, 390 px). Update the CHANGELOG entry for 0.41.0. Run the full suite and `python scripts/check.py --browser --audit`; report counts only. No branches, tags or commits.


git status
git add -A
git commit -m "Pending 0.41.0: executive view (default approver, View by tabs, column sort, Today/Tomorrow and freeze tags, sticky header, fallback to all approvers)"
git push