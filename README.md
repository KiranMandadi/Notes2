Wording/display only - no rule logic, severity or score changes. Codes and counts only.
1. CV-02 owner question names only the triggering fields, e.g. "Why do Urgency and Priority need to
   be at the top level?" (same field list as the message).
2. Q-COMPLETE-07: message uses the template question's text, not its id (e.g. "Which users are
   affected? - answered 'N/A'"); evidence shows the answer(s) that triggered it, not word counts.
3. History comparison: group day-of-week and start-hour values (consecutive hours as ranges, e.g.
   "14:00-15:00, 20:00-21:00"); ratios rounded to one decimal with "about" ("about 2.5x longer").
4. Then, check only: list up to 3 pending or recent past CRQ ids each for Emergency, Standard,
   changes on two or more platforms, and risk level 4 or 5 (ids only), so I can spot-check them.
Proof from an actual re-run: findings, scores and statuses identical on 6,461 + 16; wording diffs by
rule code with counts. Run python scripts/check.py --browser; list files changed; then stop.
No branches, tags or commits.