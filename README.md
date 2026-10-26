Quality report, UI only (no logic, no data changes):
1. Header summary under the CRQ: 2 px smaller than now, font-weight 400-500 (not semi-bold); keep
   the current colour, 2-line limit and tooltip.
2. Header field row (Product name · Planned · Change coordinator): replace equal columns with
   content-width columns and a fixed gap (about 48 px); the Planned value never wraps
   (white-space: nowrap). Long Product name or coordinator values may wrap within their own
   column. At <= 760 px the three stack as today.
3. Summary block (status ribbon): remove the Risk tile. Keep the status/next-action text and the
   Blockers, Major and Minor tiles; the three tiles share the freed width equally. Risk level stays
   in At a glance (Risk group).
Apply 1-2 to the Executive brief header too if it shares the template; do not change the brief's
own summary block. Check with the longest planned window and product name in the pending set, at
1440 px and 760 px, and print. Run python scripts/check.py --browser; list files changed; then
stop. No branches, tags or commits.