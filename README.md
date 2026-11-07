Review Decision adjustments and Pending row layout. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; never run crq login; GET requests only to Remedy; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Remove "Move to next after deciding" completely.
   - Remove the tick box, its sessionStorage setting, the 400 ms auto-step logic, and their tests and doc lines.
   - Recording a decision only records it. The admin steps manually with ‹ › or ←/→. The A/N shortcuts stay.

2. Move the decision controls off the table's results line into a slim bar above the table card, outside it, right-aligned:
   "Review decisions · Decided N of M   [Copy Decisions]   Clear"
   - "Review decisions": a small grey label.
   - "Copy Decisions": a proper button (white, 1 px #CFD7E3 border, 34 px high, copy icon). Disabled with the tooltip "No decisions yet" when there are none.
   - "Clear": a small link, with the existing confirm.
   - The results line goes back to "Sorted by … · Showing X of N" plus the search only.
   - The same bar sits above the calendar layout. On phone, it wraps under the View by panel, full width.

3. Make decision pills distinct from the Quality status pills.
   - Decision pills are outlined: white fill, 1 px border, coloured text and an icon.
     - "✓ Approved": border #7CC4A0, text #1E6B45.
     - "↻ Needs work": border #E8B266, text #8A4B08.
     - Tooltip: "Review decision: Approved" or "Review decision: Needs work".
   - Quality pills stay filled, as they are.
   - The overlay's Approve and Needs work buttons use the same outlined style when selected, keeping the button labels "Approve" and "Needs work".
   - Calendar dots use the decision border colours.

4. Pending Change cell: below the summary, add a small three-row grid with a fixed label column (about 64 px; labels 10 px, uppercase, #8592A8) and left-aligned values.
   - CLASS: the class value.
   - PRODUCT: the product, using the full remaining width of the Change column, one line. Use an ellipsis with the full name in a tooltip only if it still doesn't fit.
   - DECISION: the outlined decision pill. With no decision, show a muted "Not decided" (12 px, #8592A8, no pill).
   - Remove the decision pill from the CRQ line; that line keeps the number, the copy icon and "✓ Viewed".
   - Use the same layout in the phone cards.

5. Tests and docs.
   - Tests:
     - no auto-step remains;
     - the bar's placement and states (empty, decided, Clear confirm) in the list and calendar layouts;
     - decision pills distinct from quality pills;
     - the CLASS / PRODUCT / DECISION grid, including "Not decided", a long product name with the tooltip, and the phone layout;
     - the decision pill no longer on the CRQ line.
   - Update decisions.md, the user guide and the CHANGELOG for this version (no new version).
   - Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only.
   - Screenshots to work/preview/ at 1440 and 390 px.

Stop when done and report counts, plus the list of files changed. No branches, tags or commits.


git status
git add -A
git commit -m "Pending: Review Decision bar above table, distinct decision pills, CLASS/PRODUCT/DECISION rows; remove auto-advance and Send to owner"
git push