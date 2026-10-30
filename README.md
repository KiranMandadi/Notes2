git status --short
git add -A
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Pending page: column sorting with indicators, calendar follows status chips, summary/CRQ/product search"
git push origin main