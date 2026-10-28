Rules page, display only:
1. Purpose line: "What a good change does, rule by rule: when it applies, how much it counts and who
   owns it." - no single-word last line at 1440 px (use text-wrap: balance or widen the block).
2. Filter bar: Search, Severity and Status labels on one baseline; the three controls identical
   height, border, radius and padding (same as the Pending filters). Browser test compares their
   label positions and heights.
3. Remove the floating "73 rules" next to the tiles; header line becomes
   "73 rules · 13 rule packs · 7 owning teams".
Check 1440, 1024, 760 px and print. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.


git add -A
git status --short
git commit -m "0.24.x: MF-03 scope fix, MF-02 widened, CC-08 advisory, Rules page polish"
git push origin main