Approved. Decisions:
1. Unknown product names: warning, checked against the history database when one exists (no
   products.yaml). Rules page shows an amber "No matching changes yet" chip on a product file that
   matches no past change.
2. A local rule may be active only with promoted: {by: <team>, reference: <ticket or minutes>};
   otherwise shadow.
3. Ended suppressions: warning in crq rules validate and check.py; error only in CI behind a flag
   (e.g. --strict-expiry). Warning 30 days before the end. Rules page shows an "Ended" chip until
   the entry is removed.
4. As planned.
5. "Switched off for ..." lines always visible on the report, brief and Send to owner.
Also document (rules-authoring.md, user guide) and say on the Rules page: changes with no Product
Name get only their coordinator group's local rules.
Build as planned. Proof from an actual re-run: findings, scores, statuses and the rule-set id
identical on all past + pending; enterprise baseline unchanged. Run python scripts/check.py
--browser; list files changed; stop. No branches, tags or commits.