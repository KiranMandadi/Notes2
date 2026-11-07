Readability pass across the Console: larger secondary text and better contrast. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Global rules (define them once as shared CSS variables or type tokens, and replace the scattered sizes):
   - No text smaller than 12 px, except uppercase labels (CLASS, PRODUCT, DECISION, column headers, section kickers), which are 11 px.
   - Secondary text uses #5B6880. Use #8592A8 only for placeholders, disabled or zero-count items, and decorative separators.
   - Multi-line text uses a line-height of about 1.5.

2. Pending table:
   - CRQ 13 → 14 px; summary 14 → 15 px.
   - PRODUCT value 12 → 13 px; the PRODUCT/DECISION labels 10 → 11 px (#8592A8 is allowed for these labels only); "Not decided" 12 → 13 px in #5B6880.
   - Window line 13 → 14 px; second line ("9 h · starts in 9 days") 12 → 13 px.
   - Impact and Class lines 12 → 13 px.
   - Viewed and decision pills, and the freeze and Today/Tomorrow tags: 11 → 12 px.
   - Results line and the Review decisions bar: 13 px in #5B6880.
   - Keep the column widths. Window's lines still must not wrap at 1440 px.

3. Quality report (standalone and overlay):
   - Issue text 13 → 14 px; "Looked for…" 11 → 12 px.
   - "How to fix" 12 → 13 px in #0B5F59 on its existing pale background.
   - At a glance labels and values 13 → 14 px; section labels (CHANGE, RISK, REQUEST, SCHEDULE) 11 px.
   - Close match, Overlapping changes, Question for the owner and Full change details row text: 12 → 13 px.
   - Severity tags and the Score line unchanged.

4. Rules page: rule title 13 → 14 px; description 12 → 13 px in #5B6880; Applies-to and Status text 12 → 13 px.

5. Review page: the three feature descriptions 12 → 13 px in #5B6880.

6. Leave unchanged: page headings, the header band, the View by card counts, column headers, buttons, filter chips and nav.

7. Checks and tests:
   - Add a check that fails if any visible text is under 12 px (11 px allowed only for uppercase labels).
   - Add a check that body and secondary text meet WCAG AA contrast (4.5:1) against its background, excluding disabled and placeholder items.
   - Check Pending, the report, Rules and Review at 1440 and 1920 px: no horizontal scroll, Window still on one line at 1440 px.
   - Update the screenshots in work/preview/ and the user guide images, and add a CHANGELOG entry (no new version).
   - Run the browser tests and `python scripts/check.py --browser --audit`; report counts.

No branches, tags or commits.


git status
git add -A
git commit -m "Readability: larger secondary text, stronger contrast, shared type tokens across the Console"
git push