Bug: from the landing page "Review change" and from Pending "Open", the browser stays on the current
page with a loading state until the WHOLE report (including the overlap search) finishes - 27-29 s
for CRQ000002364299 / CRQ000002447817. Progressive loading must apply on every entry point.
1. Navigate to the report page immediately; show verdict, findings, At a glance and the brief as soon
   as they are ready (~1 s); overlaps fill in afterwards ("Checking overlaps..."). /api/report must not
   wait for the overlap search. Same for: calendar blocks, overlap links, Back/refresh, brief tab.
   PDF stays disabled until overlaps arrive (as today).
2. Batched overlap search: CHG:Associations queried per chunk of component ids (OR qualification,
   chunk size setting default 20, under the length limit), same 9-month cutoff, deduped; windows read in
   chunks of 40; list and chunk any other per-component loop. Keep the 20 s budget and "partly
   checked" note.
Measure before/after for CRQ000002364299, CRQ000002447817 and all pending, from each entry point: time
to first content and total, requests per report (median/90th/max). Proof: overlap pairs identical
(audit 100%), scores, findings and statuses identical. Browser test: landing search and Pending Open
show the report within 3 s while overlaps are still loading. Exclude cr_core/config.py and
cr_core/history/config.py from every search. Run python scripts/check.py --browser --audit; list files
changed; stop. No branches, tags or commits.