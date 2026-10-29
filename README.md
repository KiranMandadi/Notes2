Report entry points, display/navigation only:
1. First list every place in the Console that opens a change's report (button, link, calendar
   block, recent reports, overlap links, print summary, error/empty cards, back navigation) and
   which tab each opens today.
2. Then: Pending Open button and calendar blocks open the Quality report tab. Rename the Pending
   "Brief" column to "Report" (and its button label/aria-label "Open report for <CRQ>").
3. Overlap CRQ links (At a glance, brief, anywhere else) open the same tab the reader is on.
4. Landing page "Open with" switch unchanged.
5. Any other entry point: Quality report by default; list what you changed.
Update the user guide. Browser tests for each entry point's tab. Run python scripts/check.py
--browser; list files changed; stop. No branches, tags or commits.