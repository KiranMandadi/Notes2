Define "clean" as: zero mismatches for the rule, and every suspected-false finding for the rule
reviewed in work/ with a recorded reason (verifier too broad, or fixed). Update the four places.
Docs only; run python scripts/check.py; list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.27.4: docs tidy - decisions.md, roadmap, research headers, Copilot working rules"
git push origin main