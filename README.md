UI changes, Part A (Quality report, and items 3, 6, 7 also on the Executive brief). Display only: scores,
statuses and findings must stay identical on all 6,461 past + 16 pending changes. Times stay as built in
0.15.0 (ET). No branches, tags or commits; never paste the Console URL with its ?t= token; codes and
counts only.

1. Advisory section: show only the missing types (e.g. "Missing Work Detail types: Technical Design, Risk
   Assessment"); no raw list of all types; no rule ids unless Technical details is on.
2. "Compared with N similar past changes..." styled as a section heading, not link-coloured.
3. At a glance (Quality report) and the brief's compact row:
   - remove Platforms (show only with Technical details on);
   - remove Approval time; keep the "Tight for approval" / "Start has passed" chip when it applies;
   - Impact and Urgency as two separate rows;
   - add Change reason (Remedy "Reason for Change"; confirm it is in the enterprise field map and read
     live, else list a check-fields step);
   - Risk row becomes "Risk level" showing Remedy's Risk Level value exactly;
   - replace Schedule with two rows: Freeze ("No freeze clash" or the clash) and Overlaps ("None", or the
     full CRQ numbers, one per line, each a link to that change's report, with the overlap time window in
     ET; first 3 and "+N more" which expands).
4. Issues to fix table: widen the Issue column so issues wrap less (How to fix narrower).
5. Major severity tile: a slightly stronger amber tint, from the shared tokens.
6. Summary ribbon (both tabs): remove the Freeze tile; show a red "Freeze clash" tile only when there is a
   clash.
7. Header (both tabs): label "Product" becomes "Product name" (and wherever that label appears).
8. Full change details > Overview: exactly 12 fields in a 4-column grid (2 columns on narrow screens):
   Row 1: Product name | Class | Change reason | Status
   Row 2: Impact | Urgency | Risk level | Coordinator group
   Row 3: Planned | Submit date | Operational categorization | Product categorization
   Remove Requested and Impact reason; drop the empty "Type" from "Class - Type"; split categorization
   into operational and product. An empty field shows "Not filled in". Keep the amber highlight on fields
   a finding points to.
9. "Times in ET" label: show it in the header (and the brief) only when Technical details is on; hide it
   otherwise. Keep the local-time tooltip on hover in the Console. Printed and saved reports (PDF/HTML)
   always show "Times in ET", regardless of the switch.
Verify: findings/scores/statuses identical; the brief still prints on one page for all 16 pending changes;
update tests (contracts, screens, browser/print), docs/user-guide.md and docs/contracts.md; run
python scripts/check.py --browser; list files changed; then stop.
