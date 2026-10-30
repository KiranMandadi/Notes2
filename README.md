History comparison - peer quality. Measure only, change nothing until I OK. Doc counts only; ids in
work/.
1. Today: exactly how peers are chosen (signals, weights, 0.35 threshold, 10-30, cohesion gate,
   whole-product fallback). On the 56 pending: how many use close peers vs the product fallback;
   what share of peers share a CI, categorization tiers 1-3, platform/sub-type, coordinator group.
2. Proposed peers: weighted similarity from impacted CIs (strongest), categorization tiers 1-3,
   platform/sub-type, coordinator group, summary tokens and task pattern. Tiers: Close match (shares
   CIs AND type), Similar (same type and team), otherwise no comparison - remove the product
   fallback. Differences shown only when the peer set is cohesive.
3. Validate on past changes (leave-one-out, deterministic): for each past change, old vs new peers:
   cohesion of the peer set; how well the peers' usual values predict this change's own window
   length, task set/order, deployment strategy and backout approach (hit rates); and coverage (share
   of past and pending changes that still get a comparison, by tier).
4. Report per tier and overall, old vs new; propose thresholds (min peers, min similarity, cohesion)
   that keep differences meaningful, with their coverage cost. Also the report wording: tier label and
   a "why similar" line (e.g. "Same CIs 3 of 3 · Same type BATCH/PERM/JOB SCHEDULER · Same team").
Then stop. No branches, tags or commits.