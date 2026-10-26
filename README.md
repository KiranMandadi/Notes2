Check first, then fix wording (no rule logic, severity or score changes):
1. CV-02: what exactly does it test (which fields, which values count as top level, does it look
   for a stated reason)? Is Priority a Remedy field we read, and did it trigger on this kind of
   change? Answer in codes/yes-no only.
2. Rewrite the CV-02 message to state the concern and name only the fields that triggered, e.g.
   "Urgency is set to High. Say why the change needs it, or use a lower level if it doesn't."
   (if the rule looks for a reason: "Urgency is High, but the change doesn't say why it's that
   urgent."). Evidence line: each triggering field and its value. Keep the agreed fix text.
3. If Priority can trigger CV-02, show Priority in At a glance (Risk group, after Urgency).
Proof: findings, scores and statuses identical on 6,461 + 16 (wording diffs by code with counts).
Run python scripts/check.py --browser; list files changed; then stop. No branches, tags or commits.