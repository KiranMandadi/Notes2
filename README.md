MF-03 scope (accuracy fix). Measure first, then stop for my OK:
1. Proposed: MF-03 applies only to mainframe changes that promote a package - change type (tier 2)
   "Changeman Package" or "BATCH/TEMP/CHANGEMAN/SPR", or a Package ID is filled. It does not apply
   to job-scheduler (BATCH/PERM/JOB SCHEDULER) or standalone (BATCH/TEMP/STANDALONE/SPR) changes
   without a Package ID; MF-02 keeps covering those.
2. Measure in memory on all past + pending: MF-03 findings removed/added, score changes, status
   changes (Blocked -> Needs work / Ready), and pending ids whose status changes. Confirm MF-02
   applies to the job-scheduler/standalone changes MF-03 would leave.
3. Show the new applies_label and the MF-03 "how to meet" wording unchanged otherwise.
CV-08: do not narrow; add an open item "CV-08 fires on ~91% of changes - owner of Team validation to
keep, narrow or retire it". CC-08: stays shadow; add to D24 "decide CC-08 scope (non-mainframe
only?) before activating".
No branches, tags or commits.