Show the application ORR rating (display only). Read docs/research/orr-rating.md first. Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; never run crq login; GET requests only; REMEDY_ALLOW_CREATE stays off; codes and counts only in replies. No rule, score, finding or status may change.

1. Reading
   - Add field 880001551 (RF_App_PriorityORR) to the change's existing single GET; no new request. If the change field IDs are defined only in an excluded config file, stop and ask me how to add it.
   - Mapping in a reviewed YAML (next to the other Remedy field mappings, not in code): 2→1 Low, 3→2 Medium, 4→3 High, 5→4 Very High.
   - Empty → "Not assessed". Any other value (e.g. 1, 6) → "Not recognised" with the raw value in a tooltip, plus one log line (codes only). Never guess.
   - Live only; no caching.

2. Display (value format "4 – Very High")
   - Quality report, "At a glance" → RISK group: add a row "Application ORR" directly under "Risk level". Semibold only for Very High; no colour. Tooltip: "Highest ORR of the impacted applications, from the change's risk assessment in Remedy. Shown for context; it doesn't affect the score." Empty → "Not assessed" in grey. Same row in the PDF.
   - Executive brief: the same row in its risk area.
   - Pending, Risk column second line: "Impact: Minor · ORR 4 – Very High" (the ORR part semibold for Very High, normal otherwise; no red). One line at 1440 px; it may wrap as a group below 1280 px. Same in phone cards and the PDF.

3. Pending
   - View by gains a fourth option, "ORR", with tabs Very High, High, Medium, Low (plus "Not assessed" only when non-zero). The default view stays Risk. The zero-count, URL and PDF rules apply as for the other views.
   - Default sort becomes: risk descending, then ORR descending, then start ascending. Label: "Sorted by risk, then ORR, then start time". The Risk column sort uses the same tie-breakers.

4. Docs: a decisions.md entry (ORR is display-only; source field and mapping; why ORR is the second sort key: Risk Level is 3 on 69 of 71 pending changes; Risk Level equals Remedy's Aggregate Risk Value, so no separate aggregate row). Two open items: "Confirm the ORR scale with the Remedy team (level 0/Undefined?)" and "Possible shadow check: risk assessment may be out of date when today's application Priority exceeds the recorded ORR (research: 25 of 73)". CHANGELOG and minor version bump.

5. Tests: mapping (including empty and out-of-range values); label formatting; the At a glance row, the brief and the Pending display; ORR View by tabs and counts; the new sort order and its label; no scoring change (run the accuracy audit and confirm zero score differences). Run the full suite and `python scripts/check.py --browser --audit`; report counts only.

No branches, tags or commits.

git status
git add -A
git commit -m "Show application ORR rating (display only): At a glance, brief, Pending view and sort"
git push