Follow-ups on the executive Pending page (0.41.0). Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never run crq login; live data only; codes and counts only in replies.

1. Headline: with a default approver set and not fallen back, it reads "Awaiting · N changes" — the login is missing. It must be "Awaiting <login> · N changes", matching the toggle link. Add a test that asserts the login is in the headline text.
2. View card layout: put View by, search and Filters on one row (View by left; search and Filters right), and the tabs on their own full-width row beneath. Tabs never share a row with the search box. If tabs exceed the width, wrap them as a group, with no single tab left alone beside other controls. Check at 1440, 1024, 760 and 390 px.
3. Remove the sort arrows and click-to-sort from the column headers. The order is fixed: risk descending, then start time ascending, as the label says. Remove any sort code that becomes unused.
4. Under the risk value in the Risk column, add a small grey second line "Impact: <word>" (Extensive / Significant / Moderate / Minor, full Remedy value on hover), so every view shows the attribute its tabs group by. Same in the phone cards and the PDF.

Update the browser/screen tests and the CHANGELOG entry for 0.41.0 (no new version). Run the full suite and `python scripts/check.py --browser --audit`; report counts only. No branches, tags or commits.

git status
git add -A
git commit -m "Pending 0.41.0: executive view (default approver from .env, View by tabs, Today/Tomorrow and Restricted period tags, fallback to all approvers)"
git push