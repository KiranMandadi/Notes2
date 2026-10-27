Executive brief, wording/display only - no rule logic, severity or score changes.
1. "What an approver should know": when CC-05 fired, omit the generic "The window falls in a change
   freeze" item. Keep it only when an approved exception is recorded ("An exception is recorded;
   check it before deciding.").
2. Remove the "No freeze clash." line from the overlaps item (freeze status lives in the Schedule tile).
3. Status chip uses the same words as everywhere else: Ready / Needs work / Blocked (replace
   "READY FOR DECISION" and "NOT READY YET"). Headline sentence unchanged.
4. Headline next-action verbs match the finding fix text (MF-03: "name the promotion tool and
   package", not "give"). Check every rule's headline phrase against its fix text; list codes changed.
5. CV-09 counts: "Neither of the 2 open tasks has...", "The open task has..." (1),
   "None of the N open tasks has..." (all of N > 2), "N of M open tasks have..." otherwise. Same on
   the Quality report.
6. "Standard" capitalised when it means the Remedy class, in messages and headlines (CC-04).
7. Approval-timing note ("Tight for approval..." / "Not approved - planned start has passed"): hide
   for Standard class (pre-approved); keep for Normal. Same on the Quality report.
8. Comparison label: "Usually there" only when the share is at least two-thirds; between the usual
   threshold and two-thirds show "Often there (N of M)". Tile wording follows ("Worth a check"
   instead of "Something missing" in that case). Display only.
Proof from an actual re-run: findings, scores and statuses identical on 6,461 + 16; wording diffs by
code with counts. Run python scripts/check.py --browser; list files changed; stop. No branches, tags
or commits.