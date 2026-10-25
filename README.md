Part A follow-ups (display only; no branches, tags or commits):
1. Advisory: show one line only, e.g. "Missing Work Detail types: Technical Design, Risk Assessment" with the
   fix "Add a Work Detail of each missing type."; drop the duplicate sentence and "The backout plan is checked
   by Q-COMPLETE-02" unless Technical details is on.
2. Risk level value: show the number and its label, e.g. "3 (Medium)", not "Risk Level 3" (At a glance,
   Overview, brief).
3. History comparison table: align the "Note" header on the same baseline as the other headers.
4. Explain where "score N is below 40" comes from (setting and rule). In the ribbon summary, word it as
   "score N is below the minimum of 40" and show it only when it is the reason for Blocked (i.e. no Blocker
   finding); otherwise leave it out.
Run python scripts/check.py --browser; list files changed; then stop.