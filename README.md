Pending page, display only: the calendar must show exactly the changes listed in the table.
1. Calendar follows every filter: organisation, coordinator group, approver AND the status chip
   (All / Blocked / Needs work / Ready). The PDF follows the same set.
2. Header tiles and chip counts keep following organisation/group/approver only (not the selected
   chip), so the breakdown stays visible.
3. If the filtered set has no changes in the shown week, the week shows "No matching changes this
   week" (restricted-period bands still shown).
Browser tests: selecting each chip, alone and combined with a group/approver filter, gives the same
CRQ set in table and calendar. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.