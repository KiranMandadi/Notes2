   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.35.x: faster live reads, progressive loading, loading states, overlap label"
   git push origin main


   Before doing anything, read .github/copilot-instructions.md, README.md, docs/decisions.md,
   docs/open-items.md and the latest CHANGELOG entries. Summarise in 10 lines what this project is,
   the rules you must follow, and what is in progress. Change no files.


Display only - no change to data, rules, scores or findings.
1. Pending loading state:
   - Above the table while scoring: small spinner + "Scoring N of M changes..." + a thin progress bar
     (accent colour) that fills as scores arrive; removed when complete; aria-live polite.
   - Quality cells and header tiles: small 12 px spinner + "Scoring..." in muted italic (same style as
     the report's "Checking overlaps..."), replacing the grey bar; no animation under
     prefers-reduced-motion.
   - Calendar marks use a neutral grey while scores load, then take their status colour.
2. Overlap entries (Quality report At a glance and Executive brief), each overlapping change a block:
   - Quality report (narrow column): line 1 CRQ link; line 2 window; line 3 product in muted text.
     Brief: CRQ and window on one line when they fit, otherwise two lines; then product.
   - Then the label "Common components:" on its own line (small, muted), and below it each common
     component on its own line, indented and left-aligned with each other: name + " · " + class in a
     small grey tag (application/server/...). Max 3, then "+ N more components" (expandable on the
     report, plain text on the brief).
   - Never truncate the CRQ or window. 8-10 px gap between blocks; first 5 changes, then
     "+ N more changes".
   - Brief heading: "Overlaps with N other changes on the same component".
   - PDF/print: all blocks expanded, no loading states.
Check 1440, 1024, 760 px. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.