Build it with these decisions:
1. No URL or hash state for any Pending filter (approver, organisation, coordinator group, status
   chips): state lives in the page only; reload/Refresh returns to the default view.
2. Approver search on logins only, exact match after trimming spaces and ignoring case; no partial
   match, no pick list. Matches the login in APApprovers of pending rows (Approval Status2 =
   Pending), including role rows whose expanded list contains it. Result chip: "Approver: <login> ·
   N changes" (+ "(M via a role)" when any), with x to clear. No match: "No pending approval for
   '<login>'." Text box + Find button; Enter does the same.
3. Logins only - no CTM:People lookup. Console only: keep crq summary and the agents unchanged
   (add waiting_on only to the Console's own pending answer).
4. Combines with the organisation/group filters and status chips; header count, tiles, chips, table
   and Print summary follow the filtered list.
5. No approver login written to history.db, logs/, work/, reports or the debug log; the typed text
   never leaves the browser.
6. Correct docs/roadmap.md ("the Pending list does not read them yet") and the 0.13 open item;
   update docs/user-guide.md and contracts.md.
Tests: exact/case/space match, role match, no match, combined with filters, nothing in the URL.
Proof: findings, scores and statuses identical. Run python scripts/check.py --browser; list files
changed; stop. No branches, tags or commits.