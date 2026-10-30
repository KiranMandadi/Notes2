   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.28.0: closer history peers - Close/Similar tiers, any product, cohesion gate 0.7, no product fallback"
   git push origin main