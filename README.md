Display only - no change to data, rules, scores or findings.
Quality report: move overlap details out of At a glance into their own card.
1. At a glance "Overlaps" row shows one line: "N changes - see Overlapping changes" (link that
   scrolls to the card), or the existing states (None / Checking overlaps... / Partly checked - N of
   M components / No impacted components listed).
2. New card "Overlapping changes (N)" directly below At a glance, same column, full card width (no
   label column). Shown only when N > 0 (and while checking, show the card with the spinner line).
3. Each change a block: line 1 CRQ link + window (one line if it fits, else two); line 2 product in
   muted text; then "Common components:" on its own line, each component on its own line, indented,
   with its class tag kept on the same line as the last word of the name (no " · " separator); max 3
   then "+ N more components" (expandable). 10 px gap between blocks.
4. Show the first 2 changes, then a "Show N more" button (aria-expanded) that reveals the rest and
   becomes "Show fewer".
5. The "Partly checked" note appears at the top of the card when it applies.
6. Executive brief unchanged (compact one-page layout as agreed). PDF/print of the Quality report:
   all changes and components expanded.
Check 1440, 1024, 760 px and print. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.