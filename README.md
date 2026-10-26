Bug in CC-05 evidence (0.20.4): on 2478020 (Tue 3 Nov 20:00 -> Sat 14 Nov 22:00 ET) it shows
"Restricted: 5-8 Nov", but the window covers all of Wed 4 Nov. Covered restricted days must be
counted on Eastern calendar dates from the window's ET start to its ET end, inclusive of any day the
window touches. Check the same for MF-05 online-day parts. Add tests: a window starting the evening
before a restricted period; one ending just after midnight; one across the 1 Nov clock change.
Report how many past/pending evidence lines change (counts only). Display only - findings, scores and
statuses identical on 6,461 + 16. Run python scripts/check.py --browser; list files changed; stop.
No branches, tags or commits.