Build 1, 2, 3, 4, 5 and 7. Not 6: keep 4 requests in flight (add an open item to agree 6-8 with the
Remedy team). Keep overlap_search_seconds at 20.
- Live data only: the session reuses connections, never responses; the memo stays per request.
- The one session must be thread-safe, survive token expiry (re-sign in once, same as today) and
  never be shared outside the Console process.
- Progressive loading as planned: report = verdict/findings/At a glance/brief first, overlaps fill in
  ("Checking overlaps..."), saved HTML/PDF written only after overlaps; Pending = rows first, Quality
  "Checking...", one re-sort when scores arrive.
Proof: on all 92 pending, identical change values, scores, findings, statuses and overlap pairs
(373) vs 0.34.0; report timings before/after (typical report, CRQ000002481269, Pending page; time to
first content and total). Run python scripts/check.py --browser --audit; list files changed; stop.
No branches, tags or commits.