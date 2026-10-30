git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.27.4: docs tidy - decisions.md, roadmap, research headers, Copilot working rules"
git push origin main