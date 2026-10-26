Quality report: header + At a glance. Scores, rules and findings must not change.
1. Change Coordinator (data, small): add ASCHG to the enterprise field map (extensions) as a person
   field, like requester; contract + view model. Never add it to history_map.yaml or history.db.
   Re-record the enterprise baseline. No extra Remedy request.
2. Header: keep CRQ + copy and the score ring. Summary under the CRQ: brighter (about #DCE4F0,
   contrast >= 7:1 on the header), 15-16 px, up to 2 lines then ellipsis with full text in a title
   tooltip. Field row: Product name · Planned · Change coordinator, evenly spaced (equal columns,
   same label/value style). Empty coordinator shows "Not set". Requested by moves out of the header.
3. At a glance: four groups, each with a small grey uppercase label, no extra boxes:
   Change - Remedy status, Class, Coordinator group, Change reason
   Risk - Risk level, Impact, Urgency
   Request - Requested by (label unchanged), Submitted (Submit Date, ET), Lead time
   Schedule - Approval (only when shown today), Freeze, Overlaps
   Remove Submit date from Overview (now in At a glance). Keep all other values, wording and the
   local-time hover exactly as now.
4. Lead time row: count working days on the Eastern calendar, the same way CC-01 does, so the two
   never differ. Display only; CC-01 unchanged. Show how many past + pending reports' Lead time
   value changes (count only).
5. Overlaps: one overlapping change per line (number, then its window); links in the app's teal,
   no visited/purple colour.
Same on the Executive brief header if it shares the template. Update docs/contracts.md. Check at
1440 px and 760 px, light and print, Technical details on and off. Proof: scores, statuses and
findings identical on 6,461 + 16. Run python scripts/check.py --browser; list files changed; then
stop. No branches, tags or commits.