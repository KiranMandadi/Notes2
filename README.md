git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.29.x: parallel Remedy reads, shared Pending result, sticky header, Back to top, column widths"
git push origin main