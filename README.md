Part A decisions: build (a) and (e) now; not (b); (d) later if needed.
(a) Run the Remedy list and related reads 4 at a time, with one Console-wide limit of 4 requests in
    flight (shared by all users); list query as ids first, then full rows in parallel chunks. Results
    must be identical; a failed request still shows the existing error states, never a partial page
    presented as complete.
(e) Shared mode: one shared Pending result for all visitors for 10 minutes (setting
    pending_cache_minutes: 10 in reports.yaml), shown as "as of <time>"; Refresh forces a fresh read
    for everyone; held in memory only (no change text or approver logins on disk or in logs); local
    mode behaves the same. If a load is already running, a second visitor waits for it instead of
    starting another.
Also fix the quality pill overflowing its cell at exactly 826 px.
Proof: the same change ids, scores, findings, statuses and order as a sequential load on the live
pending list; report first-load and second-visitor times. Tests for the concurrency limit, the
shared cache, Refresh, and a second visitor during a load. Run python scripts/check.py --browser
--audit; list files changed; stop. No branches, tags or commits.