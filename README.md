Pending first-load speed - measure first, change nothing until I OK. Codes and timings only.
1. Work Details paging: what page size is used now; the largest the Remedy API accepts; time the
   Work Details read for the pending list at today's size vs the largest (requests and seconds).
2. Concurrency: time the full Pending read at 4, 6 and 8 requests in flight; report any 429s,
   errors or slower per-request times. Recommend the highest safe value.
3. Background warm-up (shared mode only): propose reading Pending at Console start and every
   pending_cache_minutes, only between configurable hours (default 07:00-20:00 ET, weekdays), with
   the "as of" time; Refresh still forces a read; a failed background read keeps the last good
   result and shows "as of <time> - last refresh failed"; never runs in local mode. Estimate Remedy
   requests per day.
4. Progressive load (d): estimated time to first rows with the best settings from 1-2.
Report expected times: visitor in shared mode, Refresh, local first load. Then stop. No branches,
tags or commits.