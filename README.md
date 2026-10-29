Comparison pills, display only - Quality report "Compared with ... past changes" (Note column) and
Executive brief "How this change differs from past ones" (This change column):
1. Use the same chip component and size as the severity badges: 12 px, font-weight 600, height
   22 px, padding 0 8 px, full radius, white-space: nowrap, vertically centred.
2. Shorter labels; counts stay in the Usually / Past changes column: "About 2.9× longer",
   "Often there", "Usually there", "Different", "Same".
3. Colours: amber for differences worth checking (longer/shorter, missing, different); teal for
   usual patterns (usually/often there); grey for same. No violet. Contrast >= 4.5:1.
4. Brief: the pill sits on the same line as the value ("Missing  [Often there]"); wraps below only
   at <= 760 px.
Same in print. Browser test: pill height and font size equal the severity badge's, and no pill
wraps at 1440 px. Run python scripts/check.py --browser; list files changed; stop. No branches,
tags or commits.