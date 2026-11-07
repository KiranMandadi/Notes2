Three Pending changes. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Change cell: let the PRODUCT value wrap to at most 2 lines (CSS line clamp), with an ellipsis and the full name in a tooltip only beyond 2 lines.
   - The label column stays aligned to the first line. Short names stay on one line. Same in the phone cards.
   - Revert any column-width changes made only to fit the product name if they now leave Window or ORR cramped. Window's lines must not wrap at 1440 px.

2. Zero-count values in the Class, Organisation and Group filters:
   - Unselected values with a count of 0 are disabled: greyed out, not clickable, aria-disabled="true", skipped by arrow-key navigation, tooltip "No pending changes with the current filters". Counts reflect all other filters and the search, as now.
   - Selected values always stay enabled, even at 0, showing their tick and 0 count so they can be removed.
   - "All classes", "All organisations" and "All coordinator groups" are always enabled.
   - Group popover order: groups with changes, then any selected zero-count groups, then a "Show N groups with no changes" link that expands the disabled zero-count groups. The link starts collapsed and resets each time the popover opens.
   - "Find a group" searches all groups, including hidden ones; matching zero-count groups show disabled.
   - A URL that selects a zero-count value keeps it selected and removable; never drop it silently.
   - Counts and disabled states update live as other filters and the search change.

3. Standard changes excluded by default:
   - The default Class selection is every class except "Standard". Match the Remedy value exactly. Keep the excluded list as one named constant, documented in docs/configuration.md.
   - The Class filter button (left end of the filter bar, now "Class All ▾") reads "Class All except Standard ▾" in the normal white style, not the teal "set" style, because it's the default. Any other selection, including ticking Standard, uses the existing teal style, summary and ×.
   - In the Class popover, above Done, a muted note:
     - Standard not ticked: "Standard changes are pre-approved, so they're not included by default. N pending Standard changes are hidden." N follows the other filters and the search.
     - Standard not ticked and N = 0: "Standard changes are pre-approved, so they're not included by default."
     - Standard ticked: "Standard changes are included."
   - The Class button's × and "Clear all" return Class to this default, not to every class.
   - The default applies everywhere: the headline count, the View by cards, the counts in the other filters, the table, the calendar, "Decided N of M" and Copy Decisions.
   - URL: no class parameter means the default. Any other selection, including one with Standard, is written out explicitly.

4. Tests:
   - Product wrap: one line, two lines, and beyond two lines with an ellipsis and tooltip.
   - Zero-count values: disabled in each filter; selected zero-count values still removable; "All" always enabled; the Group "Show N groups" toggle and search; the URL case; keyboard skipping.
   - Standard default:
     - excluded by default, with the button text and the note for N > 0 and N = 0;
     - ticking Standard includes it and shows the teal style;
     - × and Clear all restore the default;
     - the headline, cards and Copy Decisions follow the default;
     - URL round-trip.
   - Update the user guide, decisions.md (Standard excluded by default, and why) and CHANGELOG (no new version).
   - Run the browser tests and `python scripts/check.py --browser --audit`; report counts.

No branches, tags or commits.

git status
git add -A
git commit -m "Pending: Standard changes excluded by default, zero-count filter values disabled, product wraps to two lines, layout refinements"
git push