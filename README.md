reports/ housekeeping (D6), no change to report content:
1. In shared mode, a Pending visit does not save a summary file unless the user clicks PDF (or an
   explicit "Save" action); individual Quality/brief reports are saved only when opened, as today.
2. Automatic clean-up: delete report files older than N days (setting report_retention_days,
   default 14) at Console start and once a day; never delete anything outside reports/.
3. Recent reports list shows only files that still exist.
Tests; docs (operations, SECURITY.md data table); close D6. Run python scripts/check.py --browser;
list files changed; stop. No branches, tags or commits.

   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.31.1: shared mode serves live Remedy data, no cached Pending result"
   git push origin main


   Overlaps by impacted component, any product. Scores, findings and statuses unchanged; no caching of
Remedy data. Measure first, then stop for my OK.
New definition: an overlap is any change of ANY product whose window overlaps this change's window
or is within 1 hour, and that has at least one "Impacts" CI in common with this change. No product
condition, no same-product fallback, no "Also running in this product" line.
MEASURE (live, on today's pending list):
1. Search: for this change's Impacts CIs, read CHG:Associations restricted to recent changes (try
   change number above the lowest raised in the last 4 and 6 months, and/or association create date
   in that period), then read only those changes' windows; keep overlapping ones.
2. Requests and seconds per report (median, 90th percentile, max) at 4 in flight.
3. Coverage vs the full measurement from earlier (262 same-product + 111 cross-product pairs): how
   many found, any missed and why.
4. How many pending changes have no Impacts CI (expected 4).
PROPOSED DISPLAY (build only after my OK):
- Label "Overlaps (same component)"; each entry "CRQ... · <product> · <window> · shares <CI>
  (<class>)"; first 5 then "+N more"; same in the brief and the Pending summary calendar.
- No Impacts CI on this change: "No impacted components listed - overlaps can't be checked".
Then stop. No branches, tags or commits.