git status --short

git add -A
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'

git commit -m "0.24.x: MF-03 scoped, MF-02 widened, CC-08 advisory, history research; Rules header, history pills, Quality report as default report view"
git push origin main