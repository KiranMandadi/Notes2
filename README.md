Pending page - two parts. No change to rules, scores, findings or statuses.

PART A - speed: measure first, change nothing until I OK. Codes and timings only.
1. Time one Pending load (~120 changes) by stage: Remedy list query, per-change detail reads
   (details, Work Details, tasks, CIs, approvals), rule scoring, history comparison, freeze/overlap
   checks, rendering. Count Remedy requests and how many run in parallel.
2. Propose, with expected gain each:
   a) batch Remedy reads by record type for all listed change ids (respect the concurrency limit);
   b) in-memory cache per change keyed on Remedy Last Modified Date - re-read and re-score only
      changes modified since; Refresh forces a full reload; nothing with change text written to disk;
   c) skip the history comparison on Pending (compute only when a report opens), if it runs today;
   d) progressive load: list rows first, scores fill in as they finish; filters, sort, counts and
      calendar enabled once all rows are in, with a small progress line ("Scoring 84 of 120");
   e) shared mode: one shared result for all visitors with its "as of" time, refreshed on Refresh
      or after N minutes.
3. Report expected load time for a first load, a repeat load, and a second visitor. Then stop for my
   OK on part A.

PART B - display only, build now:
1. Sticky table header: column names and sort controls stay visible while scrolling, below the page
   header. No sticky in print.
2. "Back to top" button: appears after scrolling past the first screen, bottom-right, small and
   unobtrusive (same button style as the Console), keyboard focusable, aria-label "Back to top";
   scrolls smoothly to the top and moves focus to the page heading. Hidden in print.
3. No pagination; all rows stay on one page.
Check 1440, 1024, 760 px and print. Browser tests for the sticky header and Back to top. Run
python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.