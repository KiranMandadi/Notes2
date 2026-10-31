Measure only: overlaps across products. For the pending list, how many changes in OTHER products
overlap in time (or within 1 h) and share an Impacts CI; which CI classes (counts); how many extra
Remedy requests a per-report search by CI would need. Then stop. No branches, tags or commits.


   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.30.0-0.31.0: history keeps every CI relationship; overlaps by impacted CI; every-pair clash check"
   git push origin main