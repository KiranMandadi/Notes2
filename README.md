Pending page refinements. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Header: move "Show all approvers" (or "Show only <name>") onto the timestamp line: "as of 7 Nov 2026, 01:57 · Times in ET · Show all approvers".
   - Use a "·" separator in the same muted colour; keep the link's teal colour and underline.
   - Remove the link's old line so the header is shorter. When the amber fallback line shows, it stays below.

2. View by caption: "Grouped by ORR" (or risk level, impact, readiness), with no change count.

3. Review decisions bar: an 8 px gap to the table card (it's currently large). Right-align it with the table's right edge, with the same horizontal padding as the table's results line. Check the list and calendar layouts, and 390 px.

4. Card labels match the table's wording:
   - ORR: "4 – Very High", "3 – High", "2 – Medium", "1 – Low".
   - Risk: "5 (Critical)" … "1 (Minimal)".
   - Impact: "1 – Extensive", "2 – Significant", "3 – Moderate", "4 – Minor". Use the same format in the table's Risk column ("Impact: 4 – Minor").
   - Readiness: unchanged.
   Keep the full Remedy value in the card tooltip, the percentage and the count.

5. Remove the share line from every card, in every View by.

6. Window column: change the second line from the bare duration to "<duration> · starts in N days".
   - N is computed in ET from today; write "starts in 1 day" for one day.
   - Omit it when the Today/Tomorrow tags show.
   - Write "started" for windows already in progress.
   - Keep the freeze tags on the same line.

7. Move Class from the Change cell to the Risk column, as a third line under Impact: "Class: Normal", in the same small grey inline style as Impact.
   - Emergency and Expedited are shown in semibold dark text (#1C2A42), no colour.
   - The Change cell grid keeps PRODUCT and DECISION only.
   - Phone cards show "3 (Medium) · Impact: 4 – Minor · Class: Normal" in their risk line.
   - The Class filter is unchanged.

8. Tests:
   - the header line and link; the caption without a count; the bar spacing in both layouts;
   - card labels per view, and Impact in the table; no share lines;
   - the "starts in" text: today, tomorrow, in progress, N days, and across the DST change;
   - Class in the Risk column, with Emergency and Expedited emphasis, and no CLASS row left in the Change cell;
   - the phone layout.
   Update the user guide, decisions.md and CHANGELOG (no new version). Run the browser tests and `python scripts/check.py --browser --audit`; report counts. Screenshots to work/preview/ at 1440 and 390 px.

No branches, tags or commits.


git status
git add -A
git commit -m "Pending: compact header, card labels match table, starts-in hint, Class under Risk, tighter decisions bar"
git push