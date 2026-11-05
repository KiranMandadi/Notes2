Follow-ups on the executive Pending page (0.41.0). Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never run crq login; live data only; codes and counts only in replies.

1. View card layout
   - View by select: 10% narrower than now.
   - Search box: 30% narrower than now.
   - Tabs, search and Filters share one row when they fit (tabs left; search and Filters right). When they don't fit, search and Filters move together to the next row, right-aligned. Tabs never wrap around the search box; if the tabs alone exceed the width, they wrap as a group on their own rows.
   - Check at 1440, 1280, 1024, 760 and 390 px, with small counts and with 3-digit counts (e.g. All 120, Medium 107).

2. One approver setting, shown everywhere
   - The Approver box in the Filters panel, the headline and the toggle link all reflect the same value.
   - On load with the default approver applied: the box shows that login. "Show all approvers" empties the box; "Show only <login>" fills it with the default login.
   - The fallback (default approver has nothing pending) leaves the box empty, consistent with all approvers being shown.

3. Typing an approver
   - Find with a login: filter the full live pending list (all approvers) to that login, and set the headline to "Awaiting <login> · N changes". The toggle link then reads "Show all approvers".
   - Find with an empty box: all approvers, headline "N changes for your groups". The toggle reads "Show only <default login>" if a default is configured; otherwise no toggle.
   - Validate the login the same way as CHANGELENS_DEFAULT_APPROVER; on an invalid value show an inline message under the box and don't query.
   - If a typed login has nothing pending, do NOT fall back to all approvers. Show the table empty state "Nothing is awaiting <login> right now." with a "Show all approvers" button. The automatic fallback applies only to the configured default on page load.
   - Refresh keeps the current approver. Enter in the box triggers Find.
   - The Filters badge counts the approver as an active filter when the box is non-empty.

4. Window column: at 1440 px a two-day window ("Mon 16 Nov 23:00 → Tue 17 Nov 05:00") stays on one line; adjust column widths (narrow Change slightly if needed). Wrapping is fine below 1280 px.

Add tests for: box filled on load, toggles keep the box in sync, typed login filters and updates the headline, empty typed login, invalid login, typed login with no results (no fallback), Refresh keeps the approver, the layout rules at the listed widths. Run the full suite and `python scripts/check.py --browser --audit`; report counts only. No branches, tags or commits.