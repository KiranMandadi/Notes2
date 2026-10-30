   git status --short
   git add -A
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.25.0: template questions matched by number and version; reason phrases for no-impact claims"
   git push origin main