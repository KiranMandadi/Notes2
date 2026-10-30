git status --short
git add -A
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.27.0: Please-confirm notes for GEN-02/03, MF-02/03, CC-04; Summary searched for MF-02/03; GEN-02 and MF-06 word fixes; Work Details in history replay"
git push origin main