Approved. Display only - rules keep using the internal level; no finding, score or status changes.
1. Everywhere a Urgency, Impact or Priority value is shown (At a glance, finding messages and
   evidence, ribbon, Executive brief, Send to owner, print), show Remedy's own value exactly
   (e.g. "1-Critical", "3-Moderate/Limited", "Critical"). Keep Risk level as "<Remedy number>
   (<label>)". crq JSON: keep impact/urgency/priority as today and the *_remedy fields.
2. Messages that quote a level use the Remedy value: CV-02 names only the fields that triggered,
   e.g. "Urgency is 1-Critical and Priority is Critical. Say why the change needs them, or use a
   lower level if it doesn't."; INF-03, PCF-03, CC-05, X-04 likewise.
3. Proof from an actual re-run (not reasoning): findings, scores and statuses identical on
   6,461 past + 16 pending; wording diffs by rule code with counts.
Update docs/contracts.md. Run python scripts/check.py --browser; list files changed; then stop.
No branches, tags or commits.