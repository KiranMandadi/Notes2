Executive Pending page, round 2: compact filter bar, ORR-first view, calendar as a view. First read .github/copilot-instructions.md, docs/decisions.md, docs/open-items.md and docs/research/orr-rating.md. Build exactly what's described below.

STANDING RULES
- No git operations: no branches, tags, commits or pushes.
- Never read, search or print cr_core/config.py or cr_core/history/config.py (exclude both from every search). Never read .env.
- Never run `crq login`; never create or modify anything in Remedy (GET only); REMEDY_ALLOW_CREATE stays off.
- Live Remedy data only: no caching of pending lists or scores in shared mode. Refresh always refetches.
- No new Remedy request per change. Any field this needs (class, organisation, coordinator group, ORR 880001551) must come from the existing list query or the existing single change GET. If a field ID is defined only in an excluded config file, stop and ask me.
- No rule, score, finding or status may change.
- In replies: codes and counts only; no change text or names.
- Work in the four stages below. After each stage, run the tests, report counts, and stop for my go-ahead.

STAGE 1 — Filter bar (replaces the Filters button, the collapsible panel and the Active filters row)
One always-visible row of rounded filter buttons, in this order: Class, Date, Organisation, Group, Approver. Then a "Clear all" link (shown only when any filter or the search is set), then the search box right-aligned.
- Each button shows "<Name> <value> ▾": "Class All", "Date 9 – 12 Nov", "Group 3 groups", "Approver Kiran Mandadi". When set, the button turns teal (border #7CC4BD, background #E8F3F2) and gets a separate × that clears only that filter. Unset buttons are white with a grey border.
- Popovers open below their button. Only one is open at a time. Esc or an outside click closes it, and focus returns to the button. Fully keyboard operable, with proper ARIA (listbox/option with aria-multiselectable, radio groups, dialog).
- Class (multi-select): "All classes" first, then every value of the Remedy class field (from Remedy's list of values, not hardcoded), each with a tick box and a count. Zero-count values are dimmed but selectable. "Done" button. Summary: "All", one or two names joined by ", ", or "N classes". Selecting every value equals All.
- Date (single choice): Any date (default), Today, Tomorrow, Next 7 days, Specific date (one date picker), Date range (From and To; swap them if reversed). A change matches if its window touches any selected date in America/New_York, including windows that start earlier or end later. Show this as one line in the popover. Today/Tomorrow/Next 7 days are computed in ET at render and on Refresh.
- Organisation (single choice): "All organisations" plus the values present, with counts.
- Group (multi-select, searchable): a "Find a group" box, "All coordinator groups", then groups with tick boxes and counts in a scrolling list (max about 240 px), plus Done. Summary: "All", the single group's name (truncated with an ellipsis; full name in the tooltip), or "N groups". When an organisation is chosen, list only that organisation's groups. Drop any selected group outside it, with a one-line note in the popover ("2 groups outside this organisation were removed").
- Approver: a login box plus Find, and a "Show all approvers" link. Keep all existing behaviour: default from CHANGELENS_DEFAULT_APPROVER, display-name rule, fallback with the amber line, typed-login rules, no fallback for typed logins, validation. The button shows the display name.
- Counts are linked: each popover's counts reflect all other active filters and the search, but not its own selection.
- Search: rounded, about 300 px, placeholder "CRQ, summary or product", aria-label "Search CRQ, summary or product". Shows a `/` key hint. Pressing "/" anywhere (except while typing in a field) focuses it. Teal when non-empty.
- URL keeps every filter so a shared link reproduces the view: ?class=Normal,Emergency&date=2026-11-09..2026-11-12 (or date=today|tomorrow|next7|2026-11-09)&org=…&groups=…&approver=<login>&q=… alongside view, tab, sort and layout. Unknown or invalid parameters are ignored, never errors.
- PDF heading lists the applied filters in this fixed order: Approver, Search, Organisation, Group, Date, Class. Then the View by and tab, then the sort, e.g. "Filters: Approver Kiran Mandadi · Date 9–12 Nov · Class Normal, Emergency | View: ORR ▸ Very High | Sorted by ORR, then risk, then start time".

STAGE 2 — View by and table
- View by is a segmented control (radio group, arrow keys) with options ORR | Risk | Impact | Readiness. ORR is first and the default (?view=orr). It sits on the row below the filter bar, after a small "VIEW BY" label, then a thin divider, then the value tabs on the same row (wrapping as a group if needed). Tab rules are unchanged: counts, zero-count tabs not clickable, switch to All when the selected tab hits 0.
- ORR tabs: Very High, High, Medium, Low, plus "Not assessed" and "Not recognised" only when non-zero.
- Table columns: # | Change | Window | ORR | Risk | Quality | Report.
  - Change: CRQ (mono, semibold) with the copy icon shown on row hover and on keyboard focus; then the summary; then a line with "CLASS <value>" and "PRODUCT <value>" on one line, truncated with an ellipsis (full text in the tooltip).
  - ORR: plain text "4 – Very High", no bold, no dot, no colour. Tooltip: "Highest ORR of the impacted applications, from the change's risk assessment in Remedy. Shown for context; it doesn't affect the score." Empty → "Not assessed" (grey); out of range → "Not recognised".
  - Risk: "3 (Medium)", with "Impact: Moderate" in small grey text below. The ORR part is removed from this column.
  - Window: unchanged (date line, then duration plus Today/Tomorrow and Freeze/Freeze · exception tags on one line at 1440 px).
- Default sort: ORR descending, then risk descending, then start ascending. Not assessed / Not recognised sort after Low. Label: "Sorted by ORR, then risk, then start time". ORR is a sortable header (↕ when inactive, ↓/↑ when active), alongside Change, Window, Risk and Quality. Every tie breaks on start time. ?sort keeps working, and Quality sort stays disabled until all scores arrive.

STAGE 3 — List | Calendar
- In the dark header, left of Refresh and PDF, add a segmented List | Calendar switch (?layout=list|calendar; default list).
- Calendar layout replaces the table area at full width. Remove the week calendar from below the table. It uses the same filters and tabs as the list.
- Calendar: "Week of 9 November" with ‹ › week arrows and "N changes this week". Seven day columns, Mon–Sun, in ET. Today outlined in teal. Restricted-period days shaded, using the existing freeze calendar. Each change appears as a chip on every day its window touches: "<last 5 digits> · <start time>" on its first day and "<last 5 digits> · cont." on later days, coloured by readiness (grey "Checking" until scored). The tooltip shows the full CRQ, readiness and window, and clicking opens the report. Keep the existing legend.
- PDF always prints the list (with the heading above), whichever layout is showing.

STAGE 4 — Polish
- Loading: while the pending list loads, show 5 shimmering placeholder rows in the table's grid. While scores load, show a shimmering "Checking…" pill in Quality. Respect prefers-reduced-motion (no animation).
- Compact header: after the dark header scrolls out of view, show a slim sticky bar with the logo mark, the headline, "<View> ▸ <tab> · N shown", Refresh and PDF. Not in the PDF.
- Phone (< 720 px):
  - the filter bar scrolls horizontally;
  - popovers open as bottom sheets;
  - the segmented controls go full width;
  - tabs wrap;
  - table rows become cards (CRQ with tags, summary, window, ORR · Risk, quality, Open);
  - the calendar becomes a day-by-day list.
- Check at 1440, 1280, 1024, 760 and 390 px, with 2- and 3-digit counts, and save screenshots to work/preview/.

TESTS AND DOCS
- Tests:
  - each filter alone and combined;
  - linked counts;
  - date overlap, including windows spanning the selected day, ET boundaries and the 1 Nov 2026 DST change;
  - Organisation narrowing groups;
  - URL round-trip for every parameter, and invalid parameters ignored;
  - "/" shortcut not firing inside inputs;
  - popovers' keyboard and focus behaviour;
  - ORR default view and the default sort including Not assessed;
  - ORR column formatting;
  - calendar chips across multi-day windows and week navigation;
  - PDF heading text;
  - skeleton and reduced-motion behaviour;
  - phone layout.
- Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only.
- decisions.md: one entry for this round (filter bar replaces the panel and chips; date overlap rule; ORR default view and sort; calendar as a layout; what was removed).
- CHANGELOG, minor version bump, README Console section and user guide updated.

No branches, tags or commits.