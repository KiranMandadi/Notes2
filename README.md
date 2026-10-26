Quality report summary block, UI only: make the count cells symmetric. Each of Blockers, Major and
Minor is an equal-width cell between dividers, with the same inner padding (about 12 px) on the
left and right of every divider and at the card's right edge; the tinted box fills its cell inside
that padding, so all three boxes are the same size and evenly spaced whether tinted or not. Same
top/bottom inset for all. No other changes. Check 1/2/0, 0/0/0 and 0/2/3 at 1440 px and print.
Run python scripts/check.py --browser; list files changed; then stop. No branches, tags or commits.