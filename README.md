Overlay toolbar polish. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Light toolbar: background #FFFFFF, 1 px #E6EBF2 bottom border; text and icons #1C2A42; buttons with a #CFD7E3 border and #F4F6FA on hover; the step counter and "Next:" hint in #5B6880; the Esc keycap styled as a light keycap. Height, layout and behaviour unchanged.
2. "Next:" hint: show the last 7 digits of the change number (e.g. "Next: 2471298"), not 5. "Last in list" unchanged.
3. Remove the "← → to step" text after the hint. Keep the ←/→ keyboard stepping. Add tooltips and accessible names to the step buttons: "Previous change (←)" and "Next change (→)". Keep the Esc keycap on "Back to Pending".
4. Calendar bars: use the last 7 digits in the bar label too (e.g. "2363806 · Mon 20:30 → Wed 06:00"), truncating with an ellipsis as now when the bar is short.
5. Update the browser tests for the toolbar colours, the 7-digit hint and bar labels, the removed text, and the tooltips. Run the browser tests and `python scripts/check.py --browser --audit`; report counts. Update the CHANGELOG entry for 0.45.0 (no new version).

No branches, tags or commits.

git status
git add -A
git commit -m "Remove PDF and print support; overlay light backdrop and toolbar; 7-digit change numbers; Technical details only in report footer (0.45.0)" -m "No PDF buttons or print CSS anywhere; old print and PDF addresses return 404. Overlay uses a near-white blurred backdrop, a light toolbar, and 7-digit numbers in the Next hint and calendar bars. Also commits the updated Copilot working rules. No rule, score, finding or status changes."
git push