Freeze calendar (closes D17). Enterprise profile.
1. Replace ALL sample freeze periods in config/calendar.yaml with these restricted periods
   (America/New_York, whole days, inclusive), applying to every change regardless of risk or class
   (no risk ceiling; Emergency included):
   2026-10-26..2026-11-02, 2026-11-04..2026-11-08, 2026-11-11..2026-11-15,
   2026-11-21..2026-12-06, 2026-12-18..2026-12-31.
   (Open days: 3 Nov, 9-10 Nov, 16-20 Nov, 7-17 Dec.) A window clashes if any part of it falls on a
   restricted day. Add a comment naming the source and that the calendar ends 2026-12-31.
2. Beyond the last calendar date: Freeze shows "Freeze calendar not set for this date" (neutral grey,
   not "No freeze clash"); CC-05 does not fire.
3. Confirm how CC-05 treats a recorded freeze exception (which fields; codes only).
4. BEFORE applying: report impact as counts only - past (6,461) and pending (16): how many gain or
   lose a freeze clash, how many CC-05 findings are added/removed, and status changes
   (Ready/Needs work -> Blocked and back), plus pending change ids that become Blocked.
   Then stop for my OK.
After OK: apply, re-record the enterprise baseline, regenerate docs, close D17 in
docs/open-items.md (note: "restriction level per period to be confirmed - currently all changes").
Run python scripts/check.py --browser; list files changed; then stop. No branches, tags or commits.