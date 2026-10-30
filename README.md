Display/wording only, no rule or score changes:
1. "Please confirm" notes (GEN-02, GEN-03, MF-02, MF-03, CC-04) get their own chip "Please confirm"
   (grey outline), distinct from the "Advisory" chip used by advisory rules, in the "Worth a look"
   section, the brief and Send to owner.
2. Ribbon tag: when Remedy status is Scheduled, Scheduled For Review/Approval-complete, Implementation
   In Progress or later, use "Blocked · Found after approval" / "Needs work · Found after approval"
   instead of "Fix before review". List which Remedy statuses count as "after approval" and stop if
   unsure.
3. Check only: CRQ000002465323 gets MF-06 - which signal identified it as a Db2 change (field and
   word, no text), and is that signal reliable across past changes (count of MF-06 applicable changes
   by that signal)?
Run python scripts/check.py --browser --audit; list files changed; stop. No branches, tags or commits.