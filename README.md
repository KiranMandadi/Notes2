Time zone investigation - Phase 0 only; write docs/plans/timezone.md and stop. No code, profile or
display changes; no branches, tags or commits; codes and counts only.
1. Which time zone does each part use today, and where does it come from (Remedy API value, epoch/UTC,
   the laptop's local zone, a setting)?
   - reading dates from Remedy and storing them in history;
   - display: header, At a glance, Overview, tasks, Work Detail, approvals, Pending, brief, prints/PDF,
     Send to owner, "at the time of this report";
   - rules: freeze calendar / CC-05, CC-07 weekend, MF-05 online day / batch critical path, CC-01 lead time
     (working days), CC-06 window length, approval timing chip;
   - history notes: start hour, weekday, window, approval percentiles; calendar.yaml periods.
2. What Remedy actually returns for a date field (format and zone), checked on the 16 pending changes.
3. Impact of moving everything to US Eastern (America/New_York, EDT/EST automatic): per rule and history
   note, how many findings/notes would change on all 6,461 past + 16 pending changes, and the status split
   before/after. List 5 spot-check ids per affected rule.
4. Edge cases: changes spanning a daylight-saving switch, midnight boundaries, weekend start/end, freeze
   periods defined in calendar.yaml (what zone are they written in?).
5. Recommendation: display-only change, or display + rule fix; proposed setting in config/reports.yaml
   (display_timezone) and whether rules need a separate rules_timezone.
Then stop for my decision.