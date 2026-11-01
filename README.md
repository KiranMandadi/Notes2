   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "Restricted periods use official times: 09:00 on the first date to 21:00 on the last date (ET)"
   git push origin main