Pending table, display only: show which columns are sortable.
1. Sortable headers (Change, Window, Risk, Quality) show a small up/down chevron icon after the label
   in muted grey; "#" and "Report" show none.
2. Hover/focus on a sortable header: label and icon darken, light background, cursor pointer, title
   "Sort by <column>".
3. Active sort column: the chevron is replaced by a single arrow (up/down) in the accent colour, as
   now.
4. Icons are inline SVG with aria-hidden; aria-sort stays the source of truth. Same in print (icons
   hidden in the PDF).
Check 1440, 1024, 760 px. Browser test: sortable headers have the icon, others don't. Run
python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.