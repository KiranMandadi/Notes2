Spot-check follow-ups (0.17.0). Check first, then fix wording only. No rule logic, severity or
score changes without my OK. Codes and counts only, never change text.

A. Check and report, then STOP for my OK:
 1. History comparison: is the current change's text compared AFTER the same redaction applied to
    history (e.g. logins -> [login])? On 2473825 the Backout plan shows "Different" only because of
    this. Count past/pending "Different" notes caused only by redaction.
 2. GEN-02: which fields does it search; is the Deployment strategy pick-list value read? Why did it
    fire on 2455359 (Blue/Green) and 2473825 (Big Bang) with a strategy selected?
 3. CC-06 and MF-05: why they did NOT fire on 2460595 (9 h), 2473485 (29.5 h, Mon 13:30 start) and
    2453234 (89 h, same start as 2462054, which did fire MF-05). If an explanation in the text
    satisfied the rule, say which field (no text).
 4. Q-VAGUE-01 on 2460595 and 2473485: which phrase in the Backout plan triggered it, and is
    Q-COMPLETE-05 (backout long enough) passing on them? (codes/lengths only)
 5. Overlaps: exact definition (time only, or same CI/team/coordinator group?). Why is 2477851
    not listed on 2473485 although their windows overlap?

B. After my OK, wording/display only:
 - Comparison: apply the same redaction to the current change before comparing.
 - GEN-02 with a strategy selected: message "Its deployment strategy is <value>, but the change
   doesn't say which tool or pipeline deploys it, or the manual steps."; fix text drops "how it is
   rolled out".
 - Fix text names only the missing parts (e.g. GEN-03 when only the rollback trigger is missing:
   fix asks for the rollback trigger only). Check all rules for this pattern; list codes + counts.
 - CV-09 evidence: task names with counts (e.g. "Implementation Plan x5, Certification Plan x4").
 - Q-VAGUE-01 owner question: "What evidence supports the 'no impact' statement in the <field>?"
 - Ribbon next-action for CV-02: "say why Urgency and Priority are at the top level" (no "must be").
 - When a rule was satisfied by an explanation in the text, list it under Technical details as
   "<code> satisfied - reason given in <field>".
 - Overlaps label reflects the definition (e.g. "Overlaps (same CIs)").
 - Comparison wording: "Nothing differs from the past changes compared with." ->
   "This change matches its <N> similar past changes on every point compared."

Proof from an actual re-run: findings, scores and statuses identical on 6,461 past + 16 pending
except where I approve; wording diffs by rule code with counts. Run python scripts/check.py
--browser; list files changed; then stop. No branches, tags or commits.