Pending page filter bar - visual polish only (no logic changes). Highest-quality finish.
1. Filter row as a CSS grid: [Organisation][Coordinator group][Approver login + Find][Clear filters].
   The three fields have equal width (minmax(0,1fr)), identical height 40 px, same border colour,
   radius, padding, font size and focus ring as the rest of the Console. Find is the same height,
   joined to the login input (shared border, no gap). Clear filters is a text link vertically
   centred in the row, shown only when a filter is active.
2. Labels: same style for all three (the existing small uppercase label), on one baseline, same gap
   to their field. Use real <label for>.
3. Approver input: type="text", autocomplete="off", autocapitalize="off", spellcheck="false",
   placeholder "e.g. first.last" (no browser autofill icon).
4. Messages: "No pending approval for '<login>'." directly under the login field in small text with
   an amber field outline (aria-describedby), not under Organisation.
5. Active filters line under the row, only when any filter is active: "Active filters" label then
   one chip per filter - "Organisation: <name> ×", "Group: <name> ×",
   "Approver: <login> · N (M via a role) ×" - each × clears just that filter.
6. Header: title shows the count only, "18 of 43 changes" when filtered (unchanged "43 changes for
   your groups" when not); the filter description moves into the subtitle at normal subtitle size.
   Tiles keep following the filtered list.
7. A 1 px divider between the filter row and the status chips + Refresh/Print row; consistent
   vertical spacing (16 px) between rows.
8. <= 1024 px: two fields per row; <= 760 px: one per row, Find stays joined to the input.
   Keyboard order unchanged.
Check 1440, 1280, 1024, 760 px and print (filters print as a one-line summary). Browser test that
the three fields have equal height and width at 1440 px. Run python scripts/check.py --browser;
list files changed; stop. No branches, tags or commits.