git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.29.x-0.30.0: Pending speed and layout; history schema 4 keeps every CI relationship"
git push origin main