Approved - build in two steps. Step 1 now:
Apply proposals 1-7, 9 (relabel CV-03 "Risk Level - Computed is <n> (<label>)"), 10, 12, 13, 14
(add "LPARs"), 15 (synthetic cases first, then fixes), 16, and 11 as: keep "etc" as filler, but
never match inside paths (/etc/...) or proper names ("Misc. <Name>"). Upgrade certifi to
2026.10.18+ (regenerate requirements.lock and requirements-dev.lock, THIRD-PARTY-NOTICES.md).
Add every synthetic case from section 4 of accuracy-audit.md as permanent tests.
Make the verifier permanent: move it to scripts/accuracy_audit.py (counts and rule codes only in its
output, ids only under work/), add `python scripts/check.py --audit` to run it, and document it as
a release check in docs/operations.md.
Add D24 items: Standard changes and Deployment strategy (decision 1), which risk level CV-03 checks.
Proof from an actual re-run: findings, scores and statuses by rule code with counts on all past +
pending, matching your measurement; pending ids whose status changes; re-run the verifier and report
suspected-false and mismatch counts per rule after the fixes. Re-record the baseline, regenerate the
catalogue, CHANGELOG, version bump. Run python scripts/check.py --browser; list files changed; stop.
Do NOT build proposal 8 yet. No branches, tags or commits.