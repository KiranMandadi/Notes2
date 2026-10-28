Build "MF-03 scoped + MF-02 widened":
1. Add Package ID to the enterprise field map for live reviews (read-only, no extra Remedy request
   if it comes with the change); add applies_when keys for a categorization tier and a filled field,
   with schema, validate and tests.
2. MF-03 applies_when as proposed (tier 2 Changeman Package or BATCH/TEMP/CHANGEMAN/SPR, or Package
   ID filled); applies_label as shown. MF-02 also applies to tier 2 BATCH/PERM/JOB SCHEDULER and
   BATCH/TEMP/STANDALONE/SPR; update its applies_label.
3. Before applying, explain the 8 past Needs work -> Blocked (codes/counts: which findings take them
   below 40) and stop if any is not caused by the new MF-02 finding.
4. Add the 29 changes with neither rule (28 Software, 1 Application Data) as question 4 on
   docs/research/mf-03-package-id.md and in open items (with D16).
Proof from an actual re-run: findings, scores and statuses by rule code with counts on all past +
pending, matching the measurement; re-record the baseline; regenerate the catalogue; update
CHANGELOG (Changed: MF-03 scope, MF-02 scope) and docs. Run python scripts/check.py --browser; list
files changed; stop. No branches, tags or commits.