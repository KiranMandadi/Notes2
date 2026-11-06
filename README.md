git status
git add -A
git commit -m "Pending: List | Calendar layout; calendar moved into the layout switch"
git push

Stage 3 approved with the changes below. Apply them, then do Stage 4 and the final docs pass. Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; never run crq login; GET requests only; live data only; no rule, score, finding or status changes; codes and counts only in replies.

A. Calendar: which week opens first
1. If a Date filter is set, open on the week containing its first date.
2. Otherwise open on the current ET week if any filtered change's window touches today or a later day of this week (including changes that started earlier and are still running).
3. Otherwise open on the week of the next change starting after this week.
The week arrows still move freely.

B. Calendar: one bar per change, not one chip per day
- Lay the week out as a 7-column grid. Each change is a single bar from its first to its last day in that week (same ET day rule as the Date filter). Overlapping changes stack in lanes (first-fit by start time); bars never overlap.
- Label: "<last 5 digits> · <start day+time> → <end day+time>", e.g. "63806 · Mon 20:30 → Wed 06:00". Truncate with an ellipsis if the bar is too short. The tooltip and accessible name give the full CRQ, readiness, ORR and window. Click opens the report.
- A bar cut by the week edge shows ◂ or ▸ at that end, with "from previous week" / "into next week" in its tooltip and accessible name.
- Keep the readiness colours, grey for Checking, the amber ring for an approved freeze exception, the restricted-day shading and band, today's outline and the legend.
- "N changes this week" must equal the number of bars.
- Phone (< 720 px): a day-by-day list, with each change listed once, under its first day in the week, with its full window.

C. Stage 4: polish
- Loading: while the pending list loads, show 5 shimmering placeholder rows in the table's grid. In the calendar, show 3 shimmering placeholder bars. While scores load, show a shimmering "Checking…" pill in Quality. Respect prefers-reduced-motion (no animation).
- Compact header: once the dark header scrolls out of view, show a slim sticky bar with the logo mark, the headline, "<View> ▸ <tab> · N shown" (or "Week of 9 Nov · N changes" in the calendar), Refresh and PDF. Never in the PDF.
- Phone (< 720 px):
  - the filter bar scrolls horizontally, and popovers open as bottom sheets;
  - the View by and List | Calendar controls go full width, and tabs wrap;
  - table rows become cards: CRQ with tags, summary, window, "ORR · Risk", quality, Open;
  - the calendar follows B above;
  - no horizontal page scroll.
- Check at 1440, 1280, 1024, 760 and 390 px, with 2- and 3-digit counts, in list, calendar and loading states. Save screenshots to work/preview/.

D. Tests
- Opening week: all three cases, including a change that started before today and ends later this week.
- Calendar bars: one bar per change; spans; lane stacking for overlapping windows; week-edge markers; count = number of bars; a bar crossing the 1 Nov 2026 DST change.
- Skeletons and reduced motion; the sticky bar appearing and disappearing; the phone layout at 390 px for both layouts.
- Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only.

E. Final docs pass
- decisions.md: one entry for this round. Cover:
  - the filter bar replacing the panel and chips;
  - the date overlap rule;
  - the URL holding class, date, org, groups, view, tab, sort and layout, but never the approver or search;
  - ORR as the default view and sort;
  - the calendar as a layout, with one bar per change;
  - the opening-week rule;
  - what was removed.
- SECURITY.md: state exactly what the URL may and may not contain, and that request logs never record query strings.
- CHANGELOG, minor version bump, README Console section, user guide (with the new screenshots).

Stop when done and report counts. No branches, tags or commits.


git status
git add -A
git commit -m "Pending: calendar bars, opening-week rule, loading states, sticky header, phone layout, docs"
git push