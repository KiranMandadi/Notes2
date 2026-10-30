Approved: build item 1 (Summary searched after each rule's own fields for MF-02 and MF-03) and A2
("Please confirm", 0 points, naming the field) for GEN-02, MF-02, GEN-03, MF-03, CC-04.
Also apply both narrowings: GEN-02 "rolling" must not match "rolling back"/"rollback"; MF-06 "plan"
must not match "test plan", "backout plan" or "implementation plan" (measure the extra two as part of
the proof). Add synthetic tests for each, plus a note test per rule (field named, 0 points).
Proof from an actual re-run: findings, notes, scores and statuses by rule code with counts on all
past + pending, matching the measurement (report the extra MF-06 effect separately); pending ids
whose status or score changes; re-run scripts/accuracy_audit.py and report suspected-false counts per
rule. Re-record the baseline, regenerate the catalogue, CHANGELOG, version bump. Run
python scripts/check.py --browser --audit; list files changed; stop. No branches, tags or commits.