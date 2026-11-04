git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Reports open immediately from every entry point; batched overlap search for many-component changes"
git push origin main