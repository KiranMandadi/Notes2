Rules page header, display only - go back to the earlier layout:
1. Four equal tiles in one row, top-aligned with the "Quality rules" title (as before 0.24.2):
   Active 60 · Advisory 7 · Locked 6 · Retired 6. Locked tile keeps its own style, with a small
   sub-label "of the 60 active" and the tooltip "Locked rules can't be switched off by any group or
   product." Remove the "6 locked" sub-line from the Active tile.
2. Legend under the tiles on ONE line, right-aligned: "Rules with no status chip are active and count
   towards the score." (the locked sentence lives only in the Locked tile tooltip).
3. Keep: the one-line purpose line, the defaults note, and "73 rules · 13 rule packs · 7 owning
   teams" under the title. No floating "73 rules".
4. Header height back to what it was before 0.24.2; no empty band above the tiles.
Check 1440, 1024, 760 px (tiles wrap 2x2 at narrow widths) and print. Run python scripts/check.py
--browser; list files changed; stop. No branches, tags or commits.


git add -A
git status --short
git commit -m "0.24.x: MF-03 scope fix, MF-02 widened, CC-08 advisory, Rules page polish"
git push origin main