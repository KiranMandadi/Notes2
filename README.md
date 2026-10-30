Pending page, display only: add a text search to the second filter row (between the status chips and
Refresh/PDF), no new row and no separate label.
1. Input with a magnifier icon, placeholder "Search summary, CRQ or product", clear (x) button,
   Esc clears; same height/border/radius as the first-row fields; aria-label "Search pending
   changes".
2. Matches summary, CRQ number (with or without "CRQ" and leading zeros) and product name;
   case-insensitive, substring; applies as you type with ~200 ms debounce; client-side only.
3. Behaves like the organisation/group/approver filters: header count and subtitle, tiles, chip
   counts, table, calendar and PDF all follow it; combines with every other filter and the sort.
4. No match: table empty state "No pending changes match '<text>'." with "Clear search"; the active
   filters line shows "Search: <text> x".
5. Page state only, nothing in the URL. At <= 1024 px the search moves to its own line under the
   chips; at 760 px full width.
Browser tests: summary word, CRQ fragment, product, combined with a chip and a group, no match, clear.
Run python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.