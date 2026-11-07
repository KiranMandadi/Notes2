Change only the overlay backdrop colour to #5F6670 (still solid, no transparency or blur). Keep the overlay's 1 px #CFD7E3 border and the shadow 0 20px 48px rgba(0,0,0,0.25). Update the backdrop colour test and the 0.45.0 CHANGELOG/decisions line. Run the browser tests and `python scripts/check.py --browser --audit`; report counts. No branches, tags or commits.


git status
git add -A
git commit -m "Remove PDF and print support; overlay solid grey backdrop, light toolbar, scroll lock; 7-digit change numbers (0.45.0)" -m "No PDF buttons or print CSS anywhere; old print and PDF addresses return 404. Overlay sits on a solid #5F6670 backdrop with a light toolbar; Pending is locked while it's open and restored exactly on close. 7-digit numbers in the Next hint and calendar bars. Technical details only in the report footer. Also commits the updated Copilot working rules. No rule, score, finding or status changes."
git push