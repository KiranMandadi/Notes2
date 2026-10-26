Quality report, wording/display only (no rule logic, severities or scores change):
1. Evidence lines must add information, never repeat the finding. CV-09 (open tasks without
   scheduled start/end): evidence = the affected task names (e.g. "Tasks: ..."), or no evidence
   line if none are available. Check all rules for evidence that repeats the message and list them
   (codes + counts) before changing.
2. CC-01 fix text: "Move the window later, or, if it can't wait, raise it as an Expedited change
   and say why." Also check its how_to_meet and the ribbon next-action for any mention of
   Emergency as a way round the lead time.

3. Advisory rows: Points column shows "–" (en dash, secondary grey, same alignment as other
   points) instead of "0". Keep the "Advisory" chip.
4. Advisory sub-header: "Worth a look · doesn't affect the score" (replaces "Advisory · 0 points,
   not in the score"). Same wording in Send to owner and print.
Proof: scores, statuses and findings identical on 6,461 + 16 (wording diffs by rule code with
counts). Run python scripts/check.py --browser; list files changed; then stop. No branches, tags
or commits.