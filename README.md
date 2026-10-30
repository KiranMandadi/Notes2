git status --short
git add -A
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Pending sorting, search and calendar fixes; lighter history pills"
git push origin main