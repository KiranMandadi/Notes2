Intermittent 30 s+ reports (Mac and VM; random, even back-to-back). Likely one request hanging to
the 30 s timeout. Diagnose first:
1. Add `crq timing <CRQ> --repeat N` (N runs in one process, like the Console): per run print total
   seconds and the slowest request (stage, endpoint, seconds, new/reused, timed out yes/no, retried
   yes/no); at the end, a summary (min/median/max, number of runs over 10 s, timeouts).
2. Check the code for: requests sent on a pooled connection the server already closed (no reply ->
   waits full timeout); any lock that serialises requests on the shared session so one stuck request
   blocks others; whether the concurrency limit can be held by a request that timed out; retries after
   a timeout and their delay.
3. Report findings, then propose fixes (e.g. short connect/read timeouts for idle-reused connections
   with one safe retry on a fresh connection for GET only; never hold a lock while waiting on the
   network; per-request timing in logs/crq-ui.log for any report over 5 s). Stop for my OK.
Codes and timings only. No branches, tags or commits.