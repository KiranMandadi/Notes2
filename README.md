1. CHANGELENS_TODAY: add a settings row - "Testing only: the date ChangeLens treats as today
   (YYYY-MM-DD), so a report can be reproduced for a past day. Tests always set it; leave unset in
   normal use." (config.py:81). Not in .env.example, or commented out there if it already appears.
2. H7 and D13 stay open as they are.
3. docs/contracts.md: do a full line-by-line check now - every command, flag, JSON field, error
   code, exit code, example and version against the code. Fix what's wrong; report counts by status.
Docs only. Run python scripts/check.py --browser; list files changed; stop. No branches, tags or
commits.