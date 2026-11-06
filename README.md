Executive Pending page, round 3: search placement, View by panel, and the Quality report as an overlay. First read .github/copilot-instructions.md, docs/decisions.md and docs/open-items.md. Build exactly what's described.

STANDING RULES
- No git operations: no branches, tags, commits or pushes.
- Never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env.
- Never run `crq login`; GET requests only to Remedy; REMEDY_ALLOW_CREATE stays off.
- Live data only: no caching of pending lists, scores or reports. No prefetching of reports the user hasn't opened.
- No rule, score, finding or status may change. The Quality report's content and behaviour must stay identical.
- Keep the Host and Origin checks and the URL rule in SECURITY.md (the approver and search never go in the URL).
- In replies: codes and counts only.
- Two stages; after each, run the tests, report counts and stop for my go-ahead.

STAGE A: search placement and View by panel

A1. Search
- Remove the search box from the filter bar. The filter bar holds only Class, Date, Organisation, Group, Approver and "Clear all".
- List layout: put the search at the right end of the table's top line, on the same line as "Sorted by ORR, then risk, then start time · Showing X of N". About 300 px wide, 34 px high, rounded.
- Calendar layout: put it at the right end of the calendar's header line (after "Week of … ‹ › N changes this week"). Move the colour legend below the calendar, right-aligned.
- Unchanged: the placeholder "CRQ, summary or product", the aria-label, the "/" shortcut and its key hint, teal when non-empty, and the PDF heading listing the search.

A2. View by as folder tabs with a value panel (replaces the segmented control and pill tabs)
- Folder tabs: ORR | Risk | Impact | Readiness, along the top edge of the panel, as a radio group (arrow keys, Home/End).
  - The selected tab is raised (about 42 px tall versus 36 px), with the panel's background (#F2F5FA) and border on three sides and no bottom border, so it joins the panel.
  - It shows a small teal "VIEW BY" label before its name.
  - Unselected tabs are transparent with grey text.
  - The panel's top-left corner is square only when the first tab (ORR) is selected.
- Caption at the top right, above the panel: "Grouped by <ORR|risk level|impact|readiness> · N changes".
- Panel: background #F2F5FA, 1 px #DDE3EC border, radius 12 px, padding 12 px. The cards inside are role="tablist" / role="tab".
- Cards: fixed 172 px wide, left-aligned, 10 px gap, wrapping onto further rows at the same width. Never stretch or centre them. "All" comes first.
- Each card shows:
  - line 1: a coloured dot, the label, and the percentage of all changes right-aligned (none on "All");
  - line 2: the count, 26 px bold;
  - line 3: a 4 px share line in the value's dot colour on an #EEF1F6 track, width = share of total ("All" = 100%).
  - Nothing else: no readiness split and no extra text.
- Selected card: white background, 2 px navy (#0B1B33) border, soft shadow (0 4px 14px rgba(11,27,51,0.12)), dark text.
- Unselected cards: white, 1 px #DDE3EC border.
- Zero-count cards: dimmed, not clickable, skipped by the keyboard. If the selected value drops to 0, switch to All.
- Unchanged: the ORR default, the URL parameters (view, tab), the counts reflecting filters and search, and the PDF heading.
- Phone: 2 cards per row, with the folder tabs scrolling horizontally if needed.
A3. Compact sticky bar: give its PDF button the same icon as the main PDF button.

STAGE B: the Quality report as an overlay

B1. Opening
- "Open →", a click anywhere on a row, and a click on a calendar bar open the change's complete Quality report in an overlay on top of Pending.
- Ctrl/⌘-click or middle-click on "Open →" still opens the normal report page in a new tab.
- The overlay must show the complete Quality report, identical to the standalone page. Load the existing report page itself (same route, same server code) inside the overlay, in an "embedded" display mode that hides only the report's own top navigation. Do not build a second or shorter report view.
- Layout: fixed, inset 16 px, except a 72 px dimmed strip on the left (rgba(11,27,51,0.45)) where the list stays visible. 16 px radius, large shadow. Full screen on phone.

B2. Overlay toolbar (dark navy, above the report)
- "← Back to Pending" with an Esc hint.
- ‹ "7 of 30" › to step to the previous or next change in the list's current order, filters, tab and sort (calendar layout uses the same order). Keyboard: ← / → while the overlay has focus. Next to it, a "Next: <last 5 digits>" hint, or "Last in list" at the end. Stepping replaces the report in place.
- The Technical details switch, which drives the report's existing switch. Its state carries over when stepping and back to the standalone page as it does today.
- PDF, which runs the report's existing PDF, and × to close.

B3. Technical details and the rule panel
- With Technical details on, rule codes and the rule side panel work exactly as on the standalone page. Reuse the existing component unchanged.
- Esc order: rule panel first, then the overlay. A click on the dimmed strip closes the overlay only when the rule panel is closed.

B4. Closing and returning
- Esc, ×, "← Back to Pending", the dimmed strip, or the browser Back button closes it.
- Pending keeps its filters, View by tab, sort, layout, calendar week and scroll position exactly.
- Focus returns to the row's "Open →". That row is highlighted (background #EEF4FB, 3 px navy bar on its left edge) until another change is opened.

B5. "✓ Viewed"
- Every change opened in the overlay this session, including by stepping, shows a small grey "✓ Viewed" tag next to its CRQ in the list.
- Calendar bars get a small ✓ at the end, and the tooltip says "Viewed".
- Kept in sessionStorage for that browser tab only and cleared when the tab closes. Never sent to the server, logged or stored anywhere else. Document this in SECURITY.md.

B6. URL
- While open, the address has ?open=<CRQ> pushed as a history entry. Back closes the overlay; refresh reopens it; a shared link with ?open opens Pending with that report on top.
- Keep the other URL parameters as they are. An invalid or unknown ?open is ignored.

B7. Accessibility
- role="dialog", aria-modal, focus kept inside the overlay, a labelled toolbar, and arrow-key hints shown in the toolbar.
- The embedded report must not trap Esc: if the report or rule panel doesn't handle the key, it goes to the overlay.

B8. Performance and safety
- One report load per open or step, exactly as when opening the page today. Progressive loading (report first, overlaps after) must work the same.
- Same-origin only; the Host and Origin checks stay unchanged.
- The embedded mode is display-only: no new endpoints, no change to what the report reads.

TESTS
- Stage A:
  - search placement in both layouts; the filter bar without search;
  - folder tabs (keyboard, selected styling, square corner only on ORR);
  - fixed card width with no stretching at 1440 / 1024 / 390 px;
  - percentages and share lines adding up; zero-count cards not clickable;
  - the switch to All when the selected value drops to 0.
- Stage B:
  - opening the same change in the overlay and standalone shows the same score, findings, overlaps and freeze section;
  - the rule panel works in both, and Esc order is correct;
  - stepping ← / → follows the list order with filters and sort, and wraps correctly at the ends;
  - Pending state (filters, tab, sort, layout, week, scroll) is preserved after closing;
  - focus returns and the row is highlighted;
  - ✓ Viewed appears after opening and stepping, is gone in a new tab, and never reaches the server or logs;
  - ?open with Back, refresh, a shared link and an invalid value;
  - Ctrl/⌘-click opens a new tab;
  - progressive loading inside the overlay;
  - the phone overlay is full screen.
- Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only.
- Save screenshots to work/preview/ at 1440, 1024 and 390 px.

DOCS
- decisions.md:
  - the search moved to the results line;
  - View by as folder tabs with value cards (fixed width, left-aligned, navy border for the selected card);
  - the report as an overlay showing the complete report, with stepping, ✓ Viewed (session-only) and state preserved;
  - Quick look considered and dropped.
- SECURITY.md (?open and session-only Viewed), CHANGELOG, minor version bump, README and user guide.

No branches, tags or commits.


git status
git add -A
git commit -m "Pending: search on results line, View by panel, Quality report overlay with stepping and Viewed marks"
git push