1. Day of the week: approved as measured (weekend vs weekday, two-thirds of peers). Build it.
2. "Last time this change ran": first tell me exactly how the previous run is identified (fields,
   thresholds). If it matches the same recurring change (same summary pattern and CIs, or same
   template), show it whether or not the peer comparison has 10 peers; it should not depend on the
   peer tier. If it is only "latest change of the product", keep it removed. Report the counts that
   come back.
The affected-service row and agents' product notes stay removed when there's no comparison.
Proof: scores, findings and statuses identical; comparison diffs by kind with counts. Run
python scripts/check.py --browser --audit; list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.28.x: closer history peers, start-hour fix, weekend-only day note, one empty state"
git push origin main