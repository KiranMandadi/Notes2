git status --short
git add -A
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'

git commit -m "Replace Print with PDF: save-as-PDF button, preset file names, docs and tests"
git push origin main