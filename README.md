decisions.md corrections, docs only:
1. Line 16: the Rules tab is always visible in the top bar (after Pending); only the rule-set id and
   sources inside the page need Technical details. Find the release where this changed and cite it.
2. Line 37: mark R8 (20 hand-checked flags at 90% precision) as superseded on 2026-10-30 - a shadow
   rule is activated after measurement on every past and pending change and a clean automated
   verifier run (check.py --audit); no human labelling. Update the same rule wherever else it appears
   (rules-authoring.md, open-items.md, roadmap.md).
3. Check every other line against the current code and later lines for contradictions; list any
   found and fix them.
Run python scripts/check.py; list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.27.4: docs tidy - decisions.md, roadmap, research headers, Copilot working rules"
git push origin main