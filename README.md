Pending page layout, display only (no rule, score or sort-logic changes):
1. Column widths: Change ~40% (summary wraps to at most 2 lines, then ellipsis with the full text in
   a title tooltip; product name on its own muted line), Window ~26%, Risk, Quality and Brief
   compact. No large empty gaps at 1440 px.
2. Window cell on two lines: line 1 "start → end" (same day: "Mon 9 Nov · 20:00–23:00"; across days:
   "Thu 29 Oct 20:30 → Mon 2 Nov 12:30"); line 2 the duration followed by all window chips in a fixed
   order: Today/Tomorrow, then Freeze (red, CC-05 fired) / Freeze · exception (amber, approved
   exception recorded), then any other existing window chip. Chips wrap within the cell, never into
   the Risk column.
3. Remove the separate "Changes for your coordinator groups" card; add "your <N> coordinator groups"
   to the subtitle after the sort description, e.g. "Highest risk first, then lowest quality · your
   44 coordinator groups · as of 27 Oct 2026, 02:57 · Times in ET".
4. Confirm rows with an approved exception (e.g. 2453234, 2455359) show amber "Freeze · exception".
5. Proof set: if not already done, refresh the pending snapshot used for proofs to the current
   pending list (42), read-only, ids/codes only in reports, no change text in git; re-run the proof
   once and report counts per status.
Check at 1440 px, 1280 px, 760 px and print. Run python scripts/check.py --browser; list files
changed; stop. No branches, tags or commits.