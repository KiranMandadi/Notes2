Approved: build the MF-06 change as measured, with the second reading - "plan"/"package" counts as a
Db2 object only in a sentence that also says Db2. Bare Db2 mention -> "Please confirm" note
(0 points) with the agreed wording; "reorg" alone is not a Db2 signal. Synthetic tests for: bare
Db2 mention (note), Db2 + bind/SQL/tablespace (scored), ChangeMan "package id" with a Db2 mention in
another sentence (note, not scored), reorg of a VSAM file (no MF-06). Proof from an actual re-run
matching the measurement; re-run the audit; re-record the baseline; regenerate the catalogue;
CHANGELOG; version 0.27.2. Run python scripts/check.py --browser --audit; list files changed; stop.
No branches, tags or commits.

git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.27.2: Please-confirm chip, after-approval wording, MF-06 only for named Db2 objects"
   git push origin main