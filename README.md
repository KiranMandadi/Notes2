Pending page calendar and filter polish, display only:
1. Bug: week of 26 Oct shows "Restricted period 26 Oct – 2 Nov" starting on Tue 27; Mon 26 is not
   shaded. Bands must cover every Eastern calendar day of the period, inclusive of both ends
   (same day logic as the CC-05 evidence). Check every period in calendar.yaml against the
   rendered weeks and add a test for a period starting on a Monday and one ending on a Monday.
2. A band covering one day shows a short label ("Until 2 Nov" / "From 21 Nov") with the full
   period in the hover title; never truncated with "...".
3. Approver no match: keep the table empty-state line and the amber field outline; remove the
   duplicate message under the field (keep it as aria-describedby text for screen readers only).
4. Organisation and coordinator-group selects: full name in a hover title when truncated.
Check 1440, 1024, 760 px and print. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.

git add -A
git status --short
git commit -m "Pending page: filters by organisation, group and approver; calendar bands; polish"
git push origin main