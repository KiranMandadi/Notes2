git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.27.3: 'If it applies' label on Please-confirm notes"
git push origin main