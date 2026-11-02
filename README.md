Approved: (1) overlap_link_months 6 -> 9 in reports.yaml; (2) the audit uses the reports' own cutoff;
(3) cutoff drawn at midnight America/New_York, not the server's local date. Re-record the baseline.
Proof: scores, findings and statuses identical; 384 of 384 pairs found; report timings median / 90th
/ max. Update docs, decisions.md, CHANGELOG. Run python scripts/check.py --browser --audit; list files
changed; stop. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Overlap search: 9-month link window, audit uses the reports' cutoff, cutoff at midnight ET"
git push origin main