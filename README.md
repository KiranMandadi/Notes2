Small polish on the executive Pending page (0.41.0). Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never run crq login; live data only; codes and counts only in replies.

1. Approver display name
   - Headline with an approver applied: "<Display Name> · N changes" (drop "Awaiting"). The eyebrow "PENDING APPROVAL" stays.
   - Display name rule: if the login is 2 or 3 letter-only parts separated by dots (e.g. srinivas.sasapu, john.k.smith), show each part with its first letter capitalised and the rest lower case, joined by spaces ("Srinivas Sasapu", "John K Smith"). Otherwise (digits, underscores, hyphens, no dot, more than 3 parts) show the login exactly as stored.
   - Use the same display name in the "Show only <name>" link, the fallback line ("Nothing is awaiting <name> right now, so all approvers are shown."), the typed-approver empty state, the Active filters chip and the PDF headline.
   - The Approver box, the URL and all queries keep the raw login. No names are stored or logged.
   - Unit tests for the rule: srinivas.sasapu, SRINIVAS.SASAPU, john.k.smith, ssasapu, srinivas.sasapu2, first_last, a.b.c.d.

2. Today tag colour: background #BFD5FE, text #1E3A8A, font-weight 600. Tomorrow stays #E0ECFF / #1E40AF, weight 500. Same in the phone cards and the PDF. Check contrast is at least 4.5:1 for both.

Update the browser/screen tests and screenshots in work/preview/, and the CHANGELOG entry for 0.41.0. Run the full suite and `python scripts/check.py --browser --audit`; report counts only. No branches, tags or commits.


git status
git add -A
git commit -m "Pending 0.41.0: executive view (approver display name, View by tabs, column sort, Today/Tomorrow and freeze tags, sticky header, fallback to all approvers)"
git push


cd C:\CodeBase\changelens
crq ui --stop
git pull
pip install -e .
crq ui