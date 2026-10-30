Pending table column widths, display only (regression from 0.29.0's quality min-width):
- Change takes the remaining width (about 38-40% at 1440 px), so summaries fit on one or two lines;
- Window ~24%; Risk ~10%; Quality fixed 126 px min / ~12%; Report sized to its button, right-aligned;
- no empty gap between Quality and Report at any width.
Keep the 0.29.0 guarantee that nothing overflows its cell (re-run the width scan 760-1440 px) and the
narrow layout at <= 825 px. Same widths with the sticky header. Run python scripts/check.py --browser;
list files changed; stop. No branches, tags or commits.