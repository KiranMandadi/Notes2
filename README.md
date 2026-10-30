Pending table sorting, display only (client-side on the loaded list; no Remedy calls, no logic,
rule or score changes):
1. Sortable headers: Change (CRQ number; first click newest first), Window (planned start; first
   click soonest first), Risk (Remedy risk level number; first click highest first), Quality (score;
   first click lowest first). Second click reverses. Report column not sortable.
2. Ties keep the existing default order (highest risk, then lowest quality). Changes with no planned
   start sort last in either direction.
3. Header is a <button> inside <th> with aria-sort; small arrow shows the active column/direction;
   focus ring; keyboard Enter/Space.
4. The note above the table reflects the sort ("Sorted by window, soonest first"); a "Default order"
   link appears when a sort is active and restores it.
5. Sorting combines with all filters and status chips; the PDF follows the on-screen order. Page
   state only - nothing in the URL; reload returns to the default order.
6. Update the user guide and CHANGELOG.
Browser tests: each column both directions, ties, missing start, combined with a filter, PDF order,
default restore, aria-sort. Check 1440, 1024, 760 px. Run python scripts/check.py --browser; list
files changed; stop. No branches, tags or commits.