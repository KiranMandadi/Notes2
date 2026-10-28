Rules page, display only:
1. Header tiles: three status tiles that add up - Active 60, Advisory 7, Retired 6 - plus a small
   total "73 rules". Locked is not a separate tile: show "6 locked" as a sub-line on the Active tile
   (with the lock icon and the existing tooltip). Counts come from the catalogue, never hard-coded.
2. Filter count text: "In use" -> "Showing 67 of 73 · active and advisory"; "All" -> "Showing all
   73"; Active/Advisory/Retired -> "Showing N of 73"; with search or severity filters the same
   pattern with the filtered N.
3. Legend under the tiles: "Rules with no status chip are active and count towards the score.
   Locked rules can't be switched off by any group or product."
4. Local rules section: state "Changes with no Product Name get only their coordinator group's local
   rules." once (in the section description); remove the duplicate inside the card. The empty-state
   line uses the same font size, weight and colour as other card body text.
5. Check docs and the user guide say Advisory 7 (CC-08 added), not 6.
Check 1440, 1024, 760 px and print. Run python scripts/check.py --browser; list files changed;
stop. No branches, tags or commits.