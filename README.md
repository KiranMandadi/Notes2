Approved - build as listed (from_time / to_time keys, default 09:00 / 21:00, calendar.yaml version 2).
Proof from an actual re-run must match this measurement (22 pending + 1 past CC-05 removed, 18 ->
Ready, 4 -> Needs work; MF-05 and CC-08 identical). Re-record the baseline, regenerate the catalogue,
update CHANGELOG and decisions.md ("restricted periods run 09:00 on the first date to 21:00 on the last
date, America/New_York; touching a boundary is not a clash"). Run python scripts/check.py --browser
--audit; list files changed; stop. No branches, tags or commits.