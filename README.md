Two accuracy fixes, then stop:
1. Overlap matching by CI id: add the CI id to the relationships read in remedy_field_map.yaml and
   use it ONLY for overlap matching (name kept for display). Classification, platform and every
   rule must not read it. Re-record the baseline. Expect 373/373 pairs on today's list.
2. Single-change CI read: page through all CI rows instead of stopping at 200. List which features
   read this list (overlaps, CV-11, platform, history comparison...) and report, for the change with
   665 rows and any other over 200, what changes on its report.
Proof: scores, findings and statuses identical on all pending except where fix 2 corrects a change
with over 200 CI rows (list those ids and what changed, then stop for my OK if any score or status
moves). Run python scripts/check.py --browser --audit; list files changed; stop. No branches, tags
or commits.