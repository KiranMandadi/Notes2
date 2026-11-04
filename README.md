Pending default order, display only: highest risk first, then planned start (soonest first), then CRQ
number - all known when rows first appear, so the order never changes when scores arrive. No
automatic re-sort after scoring. Note above the table: "Sorted by risk, then start time". Quality
column sort stays available by clicking its header (enabled once scores are in). "Default order" link
restores this order. Update docs/user-guide.md and decisions.md ("Pending default order: risk, then
start time; never re-sorted when scores arrive"). Browser test: row order identical before and after
scoring completes. Run python scripts/check.py --browser; list files changed; stop. No branches, tags
or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Pending default order: risk, then start time; no re-sort when scores arrive"
git push origin main


Then on the VM, in PowerShell, update this one time the manual way:

# stop the running Console first (Ctrl+C in its window, or schtasks /End)
git pull origin main
.venv\Scripts\Activate.ps1
python -m pip install --no-deps -e .
crq ui

From the next update onward, the VM steps become:

git pull origin main
python -m pip install --no-deps -e .
crq ui --restart