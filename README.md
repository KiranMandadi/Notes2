Pending table, display only: add a copy button next to each CRQ number in the Change column.
1. Same copy icon/component as the report header's CRQ copy button; ~14 px, muted grey, 6 px after the
   CRQ, vertically centred on the CRQ text, same line; darker on hover/focus; always visible.
2. Click copies the full CRQ number; icon becomes a check with a "Copied" tooltip for 1.5 s; must not
   open the change, select the row or trigger sorting (stopPropagation).
3. Real <button>, aria-label "Copy <CRQ>", keyboard focusable with a visible focus ring, aria-live
   "Copied". Hidden in print/PDF.
4. Reuse exactly the report header's copy mechanism (already works over http://<ip>:8765); don't
   change the header.
Browser test: copy works, row not opened, print hides it. Check 1440, 1024, 760 px. Run python
scripts/check.py --browser; list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Pending: copy button next to each CRQ number"
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