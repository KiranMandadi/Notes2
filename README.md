Move docs/plans/local-rules-scopes.md to docs/archive/ (it is built), add it to
docs/archive/INDEX.md, update every link to it (docs/README.md, CHANGELOG, open-items).
Check links; run python scripts/check.py; list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'

git commit -m "0.23.0: local rules and suppressions for coordinator groups and products"
git push origin main