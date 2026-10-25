Accuracy investigation - these reports are used by directors and engineers, so findings must be
correct and evidence must not mislead. Phase 0 = investigate and measure only; write
docs/plans/accuracy-audit.md and stop. No code/profile changes; no branches, tags or commits; codes
and counts only (no change text in chat or files).

A. This case (CRQ000002456603), report only facts:
 1. MF-03 fires "no backout to the previous package" although the Backout plan contains a standard
    ChangeMan backout (Option B Backout, package id). Show exactly what text MF-03 received per field
    after template stripping and any length limits, which terms it looked for, and why none matched.
    Check specifically: (a) does template stripping remove the standard ChangeMan backout steps;
    (b) where does "3,000 characters checked" come from - is any field truncated when read from Remedy,
    stored in history, or passed to rules; (c) why is Deployment strategy searched for backout terms.
 2. Same for MF-01 (LPAR/region/subsystem) on this change.

B. Systematic audit across all active rules that report something "not found":
 3. For each such rule, on the 16 pending and all past changes: how often it fires, and a near-miss
    check - how often the searched fields contain related terms (synonyms, the rule's own words in
    other forms, standard template procedures) that suggest the item IS present. Rank rules by
    likely false-positive rate.
 4. Measure template stripping: per template block, which rules lose matching text because of it.
 5. Measure truncation: for every text field, max length in Remedy vs what we read/store/pass.

C. Evidence wording (proposal only): replace "Not found in <field links>" with a clear statement, e.g.
   "Looked for: a backout step that restores the previous package (e.g. ChangeMan backout, Endevor
   restore). Searched: Backout plan, Notes - not found." Links go only to the searched fields; never
   imply a searched field is missing. When a field IS filled, the report must never say it is missing.

D. Safety principle (proposal): a "not found" finding can only be a Blocker when the rule is certain
   (field empty, or definitive check). If the searched text is long and contains related terms, the
   finding becomes "Please confirm: <item> - we could not find it clearly" at Minor/advisory. Show the
   measured effect on statuses.
Then stop with root causes, ranked rule list, and proposed fixes.