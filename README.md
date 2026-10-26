Quality report summary block, UI only: add back the light grey vertical dividers (1 px, same
colour as the other card borders): one between the summary text and the counts (at the column
boundary), and one between each of Blockers, Major and Minor. Full inner height of the card with
a small top/bottom inset; tinted cells keep their inset box inside their divided cell. No other
changes. Check 0/0/0, 1/2/3, 0/0/5 at 1440 px, 760 px (no dividers when stacked) and print.
Run python scripts/check.py --browser; list files changed; then stop. No branches, tags or commits.