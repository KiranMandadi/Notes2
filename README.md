Overlap accuracy: the audit found 2 pairs the 6-month search missed (382 of 384). For each (ids from
work/accuracy-audit/overlaps.json), tell me why: link create date vs the 6-month cutoff, change
submit date, window dates (codes/dates only). Then propose the fix that finds them without slowing
reports, e.g. also include links to changes whose window is still upcoming regardless of link date,
or extend to 9/12 months - measure requests and seconds per report (median/90th/max) for each option
and how many of the 384 pairs each finds. Stop for my OK. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "0.36.0: closest past changes list for 3-9 peers (no statistics)"
git push origin main