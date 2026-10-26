Quality report, UI and wording only (no rule logic, severities or scores change):
1. Advisory section: render advisory items in the same table layout and column widths as Issues to
   fix (Severity | Points | Issue | How to fix). Severity = dashed "Advisory" chip (same style as the
   Rules page); Points = "0"; Issue = finding text with its evidence in grey underneath, like other
   findings; How to fix = the same fix box. Keep the "Advisory · 0 points, not in the score"
   sub-header above the rows.
2. At a glance > Overlaps: each overlapping change as a block: CRQ link (teal) on the first line,
   its window below in 12-13 px grey; about 10 px gap between blocks.
3. CV-02 wording (finding fix text and the ribbon next-action): never suggest lowering a value.
   Fix text: "Use the top levels only when the change really is that urgent or high-impact, and say
   why in the Notes." Ribbon next-action: "Say why Urgency and Priority are at the top level".
   Check every rule's fix text and next-action for the same pattern (lower/reduce a rating to pass)
   and list any others before changing them.
4. Summary block: remove the Freeze clash tile; the block shows the status/next-action and the
   Blockers, Major and Minor tiles only. Add "freeze clash" to the ribbon's subtitle line when there
   is one (e.g. "2 minor issues · nothing blocks it · freeze clash"). Freeze stays in At a glance.
Same on the Executive brief only where it shares these components. Check at 1440 px and 760 px and
print. Proof: scores, statuses and findings identical on 6,461 + 16 (wording diffs listed by rule
code with counts). Run python scripts/check.py --browser; list files changed; then stop. No
branches, tags or commits.