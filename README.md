Wording/display only - no rule logic, severity or score changes. Codes and counts only in your reply.
1. CC-05 message and ribbon next-action: period name in lowercase mid-sentence ("the restricted
   period 4 - 8 Nov"); capitalise only when it stands alone as a label.
2. History comparison, when nothing differs: "This change matches its <N> similar past changes on
   every point compared." (replaces "Nothing differs from the past changes compared with.").
3. Q-VAGUE-01 when the field is Backout plan: fix text "Write the steps that return the service to
   its previous state, or say why there is nothing to back out." (other fields keep today's fix).
4. CV-10: fix names only the misaligned end(s) (first task's start and/or last task's end);
   evidence shows task names with counts, e.g. "BATCH TEMP CHANGEMAN SPR x6, Certification Plan x6"
   (same format as CV-09), never cut off mid-list.
5. MF-05: message names every online-day part the window covers (e.g. "Fri 30 Oct 07:00-19:00 and
   Mon 2 Nov 07:00-12:30"); evidence shows those parts, not the planned start.
6. Ribbon subtitle: "freeze clash, exception recorded" when an approved exception exists.
7. At a glance: label "Overlaps" (one line), with hover "Same product, overlapping or within 1 hour".
8. Technical details "satisfied" line: include the matched reason word and up to ~60 characters of
   the sentence around it, escaped, e.g. "CC-06 satisfied - reason given in Notes: '...run longer
   due to the holiday batch dependency...'". Display only; never in Send to owner or print unless
   Technical details is on.
Proof from an actual re-run: findings, scores and statuses identical on 6,461 past + 16 pending;
wording diffs by rule code with counts. Run python scripts/check.py --browser; list files changed;
then stop. No branches, tags or commits.