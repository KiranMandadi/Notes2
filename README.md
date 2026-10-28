Pending page, display only:
1. Header subtitle: show only the active filter and "as of ... · Times in ET" (one line at 1440 px).
   Move the sort description to a small muted note above the table: "Sorted by risk, then quality".
2. Calendar: a restricted period spanning several days shows as one shaded band with the period
   named once ("Restricted period 11 – 15 Nov"), not repeated in every day box; an approved
   exception keeps its amber style.
3. Calendar change blocks: full CRQ number and summary in the hover title; click/Enter opens its
   brief (same as Open); keyboard focusable with a visible focus ring.
4. Label "Approver login" -> "Approver" (placeholder stays "e.g. first.last").
5. Approver with no match: the filter still applies. Header "0 of 55 changes", tiles and status
   chips 0, table shows one empty-state row "No pending approval for '<login>'." with a
   "Clear approver" link, calendar empty, Print summary says the same. Active-filter chip
   "Approver: <login> · 0 ×". Keep the amber field outline and the message under the field.
   Clearing the field or × restores the view from the other filters.
Tests: no-match shows 0 everywhere; clear restores. Check 1440, 1024, 760 px and print. Run
python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git commit -m "Pending page: organisation, coordinator group and approver filters; layout polish"
git push origin main