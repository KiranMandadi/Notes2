Rules page redesign + rule side panel (display and rule-pack text only). Work in two phases.

GROUND RULES (unchanged): no branches, tags or commits. No new dependencies. Console stays 127.0.0.1,
token cookie, Host/Origin checks, CSP 'self', no external requests. Change and Jira text is untrusted
and escaped. Never paste the Console URL with ?t=. Report codes and counts only, never field values or
change text. Rules, severities, conditions, word lists, scores and statuses must be identical on all
6,461 past + 16 pending changes; only the rule-set id may change (pack text changes), so re-record the
enterprise baseline, regenerate docs/rules-catalogue.md and run crq rules validate.

PHASE 0 - wording only, then STOP for my OK. Show one table (rule-pack text only, no change data):
code | new title | applies-to label | how-to-meet sentence.
1. Title: reword every rule's title to state what a good change does (e.g. "A backout plan is given",
   "Every required field is filled in", "A Normal change allows the minimum lead time",
   "A change to a secret keeps the secret value out of its text"). Keep the "why it matters" line.
   Finding messages on reports do NOT change.
2. applies_label (new optional pack field): plain words for each rule's conditions, e.g.
   "Every change", "Normal changes", "Every change except Standard", "Changes on two or more
   platforms", "Mainframe batch changes", "Mainframe changes that also touch a distributed platform",
   "Changes owned by your team's coordinator groups", "Configuration changes involving a secret",
   "Non-mainframe changes that mention a database script". It must describe exactly what the
   condition does - no more, no less. Fall back to today's generated text if absent.
3. how_to_meet (new optional pack field): one sentence telling the owner what to add. Draft it ONLY
   from that rule's "Looked for" list; never ask for anything the rule doesn't search for.
   Example MF-03: "Name the promotion tool and the package (for example a ChangeMan or Endevor
   package) in the notes or the backout plan, and say how the previous load modules are restored."
4. Pack display_name (new field): Core quality, Classification, Change class and calendar, Common
   validation, General application, Team validation, Mainframe, Configuration, Database,
   Infrastructure, Cloud Foundry (PCF), Microservice, Cross-platform. Optional pack note, e.g.
   General application: "Applies to every change not identified as mainframe. Each rule runs only
   when the change text mentions its topic."
5. team-validation owner "Sample-Team": show "To be confirmed" (amber) until set; add to open items.
Also list MF-06's current title, severity and conditions so I can confirm them.

PHASE 1 - build (after my OK). Update the schema, rulefile loader, validate, tests and
docs/rules-authoring.md for the new fields.

A. Rules page (Console Rules tab):
- Header: title, one-line purpose, "13 rule packs · N owning teams". Tiles: Active 60 (count
  towards the score) · Advisory 6 (shown on reports, 0 points) · Locked 6 (no product can switch these
  off) · Retired 6 (kept for the record, not applied). Rule-set id only with Technical details on.
- Filter bar: search (code, title, why, applies-to), Severity All/Blocker/Major/Minor, Status
  Current/Active/Advisory/Retired, "Showing N of 72". Client-side only.
- Left list of sections (Global, Organisation, Platform, Product) and packs with live-rule counts,
  linking to each pack; stacks above the content at narrow widths (not sticky).
- Pack card: display name, version tag, "N rules · N advisory · N retired", owner on the right, note
  if any. Source document/Confluence pages once per pack, only with Technical details on. Remove the
  per-row Owner and source column.
- One fixed column layout for every pack: Rule (mono, never wraps) | What a good change does (title +
  grey why line) | Severity (badge, same colours as reports; e.g. "Major at High risk" under it) |
  Applies to (applies_label) | Status. Status: Active with tick; "Advisory · 0 pts" dashed chip;
  lock icon "Locked" with tooltip; tunable limit tag e.g. "Limit 3-10 days". Never "shadow" in UI.
- Retired rules hidden under "Show N retired rules" per pack (aria-expanded); retired reason line says
  what replaced it where known (e.g. "Replaced by GEN-01").
- Product rules and suppressions: one card with one sentence when empty.
- Deep link: Rules page opens at #rule=<CODE>, scrolls to it and highlights it briefly.
- Print: all packs expanded including retired, no filters, no side list.

B. Rule side panel (Quality report; also Pending and Executive brief wherever a rule code shows):
- Each finding's rule code becomes a button that opens a right-side panel (about 440 px, full height,
  light backdrop; report stays visible). role=dialog, aria-modal, labelled by the title; focus moves
  into it, Tab is trapped, Esc / X / backdrop closes, focus returns to the code.
- Shows: code and pack (name + version), title, why, Severity badge, Status (+ Locked), Applies to,
  Owner, Effect on score ("-40, and any Blocker makes the change Blocked" / "-20" / "-5" /
  Advisory: "No effect on the score"), "How to meet it" box (hidden when how_to_meet is absent),
  link "View in the rules catalogue" to the Rules page #rule=<CODE>. Source only with Technical
  details on.
- Send to owner: add the how_to_meet sentence under each finding when present. crq JSON: add
  "how_to_meet" to each finding (null when absent); update docs/contracts.md.
- Panel content comes from the loaded rule packs, never from change text.

CHECKS: python scripts/check.py --browser plus browser tests for: codes never wrap; columns align
across packs; search and filters; retired toggle; Technical details hides sources and rule-set id;
#rule= deep link; print expands everything; layout stacks at about 760 px; panel keyboard (open,
trap, Esc, focus return) and ARIA; text with <script> in a finding is escaped. Proof table: scores,
statuses, findings and severities identical on 6,461 + 16; new rule-set id; baseline re-recorded.
Bump the version, update CHANGELOG.md and docs/user-guide.md. List files changed; then stop.