History CI links, then overlaps by impacted CI. Scores, findings and statuses must stay identical
throughout. Codes and counts only. No branches, tags or commits.

STEP 1 - history fix: plan only, then STOP for my OK.
- Today ci_links keeps one row per change and CI (INSERT OR REPLACE), so a CI linked both "Impacts"
  and "Related to" loses one link (past Impacts coverage 28-30% vs 96% on pending).
- Plan: key ci_links on (change, CI, relationship type) so every link is kept; schema version bump
  and migration note; loader and history docs updated.
- List everything that reads ci_links (peer similarity, "Last time this change ran", usual-CI
  profile, history replay, research scripts, audit) and how each should use relationship type
  (Impacts only, or any relationship).
- I run the history reload myself; tell me the exact command.

STEP 2 - after my reload: re-measure and report, then STOP.
- Past Impacts coverage by quarter (expect close to pending).
- Peer comparison: tiers (Close/Similar/none), cohesion and the validation figures, before vs after.
- "Last time this change ran": shown past/pending, and how many pick a different run.
- Distinct Impacts CI classes in history and pending, with counts.

STEP 3 - build the overlap change (after my OK on step 2):
- Two changes overlap when their windows overlap or are within 1 hour AND they share at least one
  CI linked as "Impacts". Every CI class counts (application, server, database, middleware,
  network, product, any other); the class only labels the entry and never filters it.
- Map the CI class (Form Name01 -> ci_class in remedy_field_map.yaml; re-record the baseline).
- Label "Overlaps (same impacted CI)"; each entry "CRQ... · <window> · shares <CI name> (<class in
  plain words>)", unknown classes shown as "(configuration item)".
- If either change has no Impacts CI: fall back to the same-product match, listed after the shared
  entries and marked "same product (no impacted CI to compare)"; never folded away.
- Same-product changes with no shared Impacts CI: one collapsed line "Also running in this
  product: N other changes", expandable.
- Same matching in At a glance, the brief's "What an approver should know", and the summary
  report's calendar (switch it to the every-pair check).
- Batched CHG:Associations read for neighbours (1-2 extra requests per report) is fine.
- Update contracts.md (schedule: shared CIs, match type, also-in-product count), user guide,
  CHANGELOG, version bump.
- Proof: scores, findings and statuses identical; overlap counts per pending change before/after.
  Run python scripts/check.py --browser --audit; list files changed; stop.