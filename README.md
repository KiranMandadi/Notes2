Display only - no change to data, rules, scores or findings.
1. At a glance: label "Overlaps" (one line), hover "Same component, overlapping or within 1 hour".
2. Each overlap entry names the first shared CI and "+N more CIs" (full list in the hover); same in
   the brief.
3. Loading states:
   - Pending Quality cells and the header tiles (Blocked / Needs work / Ready): replace "Checking..."
     and "..." with a skeleton bar (rounded, pill-sized, light grey, slow 1.5 s shimmer, low contrast);
     aria-busy="true" with visually-hidden "Loading"; no shimmer under prefers-reduced-motion.
   - Report Overlaps row and the brief's overlaps point: small 12 px spinner in muted teal + "Checking
     overlaps..." in italic muted grey; same reduced-motion rule.
   - Values fade in (~150 ms) when they arrive. PDF/print never shows loading states.
Check 1440, 1024, 760 px. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.