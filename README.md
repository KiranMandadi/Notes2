Follow-ups on the executive Pending page (0.41.0). Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never run crq login; live data only; codes and counts only in replies.

1. One-row view card
   - Remove the stacked "VIEW BY" label. Use an inline compact select reading "View by: Risk ▾" (label inside or immediately left, same height as the tabs), 10% narrower than now.
   - Order on one row: View by select, tabs, then search and Filters right-aligned. Tighten tab padding slightly if needed (keep 32 px min height and visible focus rings).
   - Must fit on one row at 1440 px with 2-digit counts. If it doesn't fit (narrower screens, 3-digit counts), search and Filters move together to the next row; the select and tabs never split. Verify at 1440, 1280, 1024, 760 and 390 px with small and 3-digit counts; save screenshots to work/preview/.

2. Zero-count tabs
   - A tab whose count is 0 stays visible (dimmed) but is not clickable: aria-disabled="true", no hover or pointer cursor, skipped by arrow-key navigation, and clicks do nothing. Its tooltip still shows the full Remedy value plus "· none pending".
   - "All" is never disabled.
   - If the selected tab drops to 0 (Refresh, approver change, search, filters, or scores arriving in Readiness), switch to All and keep the URL in step.
   - In Readiness, "Checking" disappears once all scores have arrived, rather than showing 0.

3. Restore the freeze tags in the Window column
   - Bring back the previous pair: the freeze-clash tag and the freeze-exception tag, with the same wording, colours and conditions the page used before 0.41.0 and the same wording the Quality report uses for CC-05. Take both from CC-05's own result (no second overlap check): clash without approved exception → freeze tag (amber); clash with an approved exception → exception tag (as before); touching a boundary → no tag.
   - Remove "Restricted period" if it now duplicates the freeze tag. Update decisions.md to replace the earlier tag rule.
   - Keep Today/Tomorrow (scheduled start on today's / tomorrow's date in America/New_York, or the window already in progress for Today).
   - Report, for the current live pending set (all approvers), counts only: rows expected Today, Tomorrow, freeze and exception vs rows showing each. They must match.

4. Column sorting
   - Sortable headers: Change (CRQ number), Window (start time), Risk (risk, then start), Quality (Blocked < Needs work < Ready, then score). Click toggles ascending/descending; aria-sort set; the arrow shows only on the active column.
   - Default remains risk descending, then start ascending. Ties always break on start time ascending.
   - The label reflects the active order, e.g. "Sorted by quality, lowest first", with a "Reset" link when not default.
   - Quality is sortable only after all scores have arrived; until then its header is disabled with the tooltip "Available when quality checks finish". No row moves while scores load.
   - Keep the sort in the URL (?sort=quality-asc) alongside ?view; Refresh and approver changes keep it.
   - The PDF follows the current sort and states it.

5. Tests and checks
   - Add or update tests: layout at the listed widths; zero-count tabs not clickable or focusable, and the switch to All when the selected tab drops to 0; tag counts vs CC-05, including exception and boundary cases; each sort and direction; Quality disabled while loading; URL round-trip for view and sort.
   - Update the CHANGELOG entry for 0.41.0 (no new version).
   - Run the full suite and `python scripts/check.py --browser --audit`; report counts only.

No branches, tags or commits.