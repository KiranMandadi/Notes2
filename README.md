K10: add a time budget for the overlap search (setting overlap_search_seconds, default 20, in
reports.yaml). Search components in a stable order; when the budget runs out, keep what was found and
show "Overlaps partly checked: N of M components searched - some clashes may not be shown" (report,
brief, Pending calendar card). Never show "None" for a partial check. Report on today's pending list
how many hit the budget (expect 0) and the time for CRQ000002480993. Scores, findings and statuses
unchanged. Run python scripts/check.py --browser --audit; list files changed; stop. No branches,
tags or commits.


git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.33.x: overlaps by impacted component across products, matched by CI id; full CI read; search time limit"