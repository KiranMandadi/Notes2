Wording/display only - no rule logic, severity or score changes. Codes and counts only.
1. CV-03: message "Risk level is <Remedy number> (<label>)." Evidence "Risk level: 4 (High)" (same
   wording as At a glance, never "computed"). Fix: "Check the answers to the risk questions; if the
   risk really is 4 or 5, confirm it in the Notes."
2. CV-11 evidence shows what the rule checked ("Impacts relationships: none"), not Affected services.
3. "Last time this change ran": when Backout plan is "Different", show the first differing words
   (escaped). If the only difference is whitespace, case or masking, show "Same". Explain why
   2469445's backout plan was "Different" (codes only).
4. CC-06 and MF-05 on an Emergency change: append "For an Emergency change, say why it can't wait for
   a better window." to the message.
5. Check only: on 2477975, why MF-05 and CC-06 did not fire (which reason/field, no text). On
   2477368 (risk 4), did Q-COMPLETE-07 check questions 6-8 and were they answered?
6. Rules page and side panel: CL-03 and X-01..X-06 show "Not applied yet: only mainframe is
   identified with confidence, so no change is on two or more platforms" (as MS-04); add an open
   item linked to D10/D11.
Proof from an actual re-run: findings, scores and statuses identical on 6,461 + 16; wording diffs by
rule code with counts. Run python scripts/check.py --browser; list files changed; then stop.
No branches, tags or commits.