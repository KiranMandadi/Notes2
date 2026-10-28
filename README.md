Phase 1 accepted. Correction: "review questions" means the manual review question per bad change -
"what in its record should have warned us?" - not the Details template. Keep the packet; add a
column "scored findings" and sort the 19 bad changes with no scored finding first.

Phase 2 (research only, same rules: work/research for ids, doc with counts only, read-only db):
1. Calibrate the ChangeLens defaults (D24) from history: overrun, broad and rework rates by planned
   window length bands (<=4h, 4-8, 8-12, 12-24, 24-48, >48 h) and by lead-time bands (working days
   0,1,2,3,4-5,6-10,>10), within risk level and class; say where the rate clearly steps up, with
   counts and the recent-quarter check.
2. Evidence cards for the rules with a signal: MF-03, CV-02, CC-06, CV-03 (and Q-VAGUE-01 on
   reschedule): plain-language finding ("changes where X went Y times as often..."), counts, ratio,
   recent quarter, scope, 5 example ids in work/ only.
3. Leads from Phase 1: GEN-03 within non-mainframe changes; Q-COMPLETE-01 within Normal changes;
   mainframe vs non-mainframe; risk level 4-5 not confirmed.
4. CV-08 and CV-11: they fire on 91% and 70% of changes - which sub-conditions fire most, and does
   any sub-condition alone show a signal? Recommendation: keep, narrow or retire.
5. New candidate patterns (deterministic, explainable): presence of tasks/Work Detail types/CI
   links, text sections (validation step, smoke test, rollback time, on-call contact) in
   Implementation/Backout plans, approval timing vs start, reschedule count, start hour/day, risk vs
   impact mismatch. Only those with >= 10 bad events on the fired side, holding in the recent
   quarter and within risk level.
6. Per product and per coordinator group: rates for strict, broad and rework with counts; list
   groups/products clearly above their peers (>= 30 changes) as candidates for local shadow rules.
7. Add open item: "Store findings and record snapshot at submission time (first time a change
   reaches Request For Authorization), so future research is not biased by rework edits."
Then stop with the evidence cards and a ranked candidate list. No branches, tags or commits.