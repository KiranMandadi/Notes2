Performance - measure first, change nothing until I OK. Live data only; no caching between visits.
1. Profile one report (a 1-CI change, a 5-CI change like CRQ000002481269) and one Pending load:
   time per stage and per request type, number of requests, connection setup time.
2. Check: does the Remedy client reuse HTTPS connections (keep-alive / one session)? Measure with
   and without.
3. Overlap search: can one CHG:Associations query cover several CIs (OR qualification, chunks of
   e.g. 20 ids)? Requests and seconds before/after for the two changes above.
4. Field lists and page sizes: are we requesting only the fields used? largest page size Remedy
   accepts for Work Details and relationships; effect on time.
5. Concurrency 4 vs 6 vs 8: per-request time and any errors/429s.
6. Progressive loading plan: report shows verdict/findings/At a glance first, then overlaps and
   history comparison fill in with a progress line; Pending shows rows first, scores fill in. Time
   to first content vs total.
Report expected times before/after for: report (median, worst pending), Pending page, the 5-CI
change. Then stop. No branches, tags or commits.