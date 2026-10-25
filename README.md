Follow-ups + Part B (Executive brief). Display only: scores, statuses and findings identical on all 6,461 past
+ 16 pending. Times stay ET as built. No branches, tags or commits; never paste the Console URL with its ?t=
token; codes and counts only.

FOLLOW-UPS
5. Approval row in At a glance (Quality report) and the note under the brief's Schedule tile - wording that
   explains itself:
   - "Not approved - planned start has passed (<day date time>)"
   - "Tight for approval - starts in <n> h; approvals for this product usually take up to <p75> h"
   - no row/note when there is enough time.
6. Singular/plural: "1 working day" (issue text and Lead time) and similar counts everywhere.
7. Task timing evidence: "<n> open tasks have no scheduled start or end"; do not repeat task names; list
   distinct task names once only with Technical details on.

EXECUTIVE BRIEF
B1. "What an approver should know": plain language only - the finding sentence plus an action ("Ask the
    owner to ..."); no severity points, "Looked for" or "Searched" text; fix the double full stop.
B2. Schedule tile: date and time (e.g. "Tue 10 Nov 01:30"), with duration and freeze status beneath
    ("25 h 30 min - no freeze clash"), plus the approval note from item 5 when it applies.
B3. Risk tile: show "Risk level <n> (<label>)" instead of the platform chip (platform only with Technical
    details).
B4. Compact facts row: Class | Change reason | Impact | Urgency | Coordinator group | Status.
B5. Overlaps point: "same product" (not service), full CRQ numbers as links (plain text in saved files) with
    overlap times.
B6. A single minor point reads "It doesn't block a decision." (plural wording only when several).
B7. Remove "N advisory point(s), not scored" from the brief.
B8. Remove the outcomes sentence ("Based on N completed changes ... went fine ...").
B9. "How this change differs from past ones" heading styled as a heading, not link-coloured.
"Times in ET" shows only with Technical details on; printed/saved reports always show it.
The brief must still print on one page for all 16 pending changes.

Verify; update tests (contracts, screens, browser/print), docs/user-guide.md, docs/contracts.md, CHANGELOG
and version bump; run python scripts/check.py --browser; list files changed; then stop.