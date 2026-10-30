"Last time this change ran": drop the "product has at least 10 past changes" condition for this row
only; add "shares at least one CI when both changes list CIs" to the match. Report counts: shown past
and pending before/after, and how many of the 185 and the 62 pass the CI condition. Display only;
same proof; run python scripts/check.py --browser --audit; list files changed; stop. No branches,
tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.28.x: closer history peers, start-hour fix, weekend-only day note, one empty state, last run matched by summary and CI"
git push origin main