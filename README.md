Two spacing tweaks on Pending. Same standing rules; no git operations unless I ask.
1. The gap between the View by panel and the Review decisions bar matches the 8 px gap between the bar and the table (both layouts; phone unchanged).
2. Column widths at 1440 px: give the Change column more room, taken from ORR (fit "4 – Very High" plus padding) and Window (fit the longest window line plus tags), so typical product names show in full. Window's lines must still not wrap at 1440 px; check 1280 and 1024 px too.
Update the screenshots and any layout tests; run the browser tests and the audit; report counts. No branches, tags or commits.

git status
git add -A
git commit -m "Pending: compact header, card labels match table, starts-in hint, Class under Risk, tighter decisions bar and column widths"
git push