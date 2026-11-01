Display only. Executive brief, "Overlaps with N other changes" point:
1. On screen, show the first 2 changes, then a "Show N more" button (aria-expanded) that reveals the
   rest and becomes "Show fewer" - same behaviour and style as the Quality report's Overlapping
   changes card.
2. PDF/print unchanged (compact one-page layout; "+ N more changes - see the Quality report" when it
   doesn't fit).
3. Remove the " · " before the class tag in the brief, so it matches the report card (tag on the same
   line as the last word of the component name).
Run python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.

   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.35.x: faster live reads, progressive loading with stage text, Overlapping changes card, compact brief overlaps"
   git push origin main