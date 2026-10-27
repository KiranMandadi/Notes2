Pending page, display only (no rule, score or sort-logic changes):
1. Window column: same day -> "Mon 9 Nov · 20:00–23:00 · 3 h"; across days -> "Thu 29 Oct 20:30 →
   Mon 2 Nov 12:30 · 89 h". Always include the month. ET as elsewhere; local time on hover as today.
2. Freeze chip: red "Freeze" when CC-05 fired; amber "Freeze · exception" when an approved exception
   is recorded; none otherwise. Same states and colours as the reports.
3. Risk column: "<Remedy number> (<label>)", e.g. "3 (Medium)". Subtitle: "Highest risk first, then
   lowest quality" (describe the existing sort exactly; tell me if it differs).
4. Replace the single-option "Show changes for: My groups" control with a plain line "Changes for
   your <N> coordinator groups" until there is a second option.
5. Product name on its own muted line under the summary (not joined with " · ").
6. Optional tag next to the window: "Today" if it starts today (ET), "Tomorrow" if tomorrow.
7. Proof set: the pending snapshot used for proofs has 16 changes but 42 are pending now. Refresh it
   read-only (codes/ids only in reports; no change text in git) and re-run the proof once; report
   counts per status.
Check at 1440 px, 760 px and print. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.