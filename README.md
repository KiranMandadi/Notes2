Comparison of past changes - redesign. Phase 0 = analysis, design and measurement only. Write
docs/plans/comparison-key.md and stop. No code, profile or history changes; no branches, tags or
commits; codes and counts only. There is NO human reviewer and no manual ground truth: the tool must
decide automatically and deterministically (no AI/LLM) which past changes are comparable.

Context: "service" in ChangeLens is Remedy's Product Name. A product can contain applications of
different nature (mainframe, PCF, Java...), so comparing with every past change of the product mixes
unrelated work. History must compare like with like.

1. Inventory - every use of "service"/product: the Remedy field behind it (field map, history map,
   schema); history comparison rows, approval timing, platform service pattern, "last time this change
   ran", overlap check, Pending grouping, track record, Create suggestions (backout, deployment,
   affected services, task order), service rule files/suppressions/parameters, history cache keys,
   agent instructions, report/brief wording ("Service" label).
2. Mixing - number of products; per product: change count, identified-platform mix, implementer
   support groups, operational tier 2 values; how many products are mixed (2+ groups with >=20% share).
3. Design: closest past changes within the product. For each change, score every past change of the
   same product using signals already in Remedy/history, e.g.: same implementer support group; overlap
   of linked CIs (Impacts/Related, Jaccard); same identified platform/sub-type; same operational tiers;
   summary similarity (existing text similarity, template text stripped); task-name overlap; similar
   change class. Propose weights, a minimum similarity, and K (e.g. up to the 30 most similar, at least 10).
   Must be deterministic, explainable and fast (reuse the history cache; no extra Remedy requests).
4. Alternatives to compare against: (a) product only (today), (b) product + implementer support group,
   (c) product + identified platform, (d) product + support group + platform, (e) primary Impacts CI
   (define a deterministic pick), (f) the closest-K design from step 3.
5. Measure each alternative WITHOUT manual labels:
   - cohesion of the comparison set: spread of planned window (IQR/median), task-set similarity, share
     with the same backout approach and deployment strategy, CI overlap;
   - coverage: share of changes with >=10 comparable past changes;
   - agreement between independent signals (support-group grouping vs CI grouping);
   - leave-one-out check on past changes: how well each alternative's "usual" values (median window,
     usual tasks, usual backout/deployment, approval p75) predict the change's own values;
   - accuracy impact: on the 16 pending changes and 300 sampled past changes, how many history notes
     (x-longer, missing/always-there, different, affected CIs, approval tight) appear, disappear or change.
   - time added per report.
6. Recommendation, decided by the measurements: the method, thresholds, and fallback chain (e.g.
   closest-K if >=10 similar enough; else product + support group; else product; else "Not enough
   comparable past changes" and no history notes). Rules:
   - show history notes only when the comparison set is cohesive enough (threshold from the data);
   - the report states what it compared with, e.g. "Compared with 24 similar past changes of <product>
     (same team and CIs)"; with Technical details on, list the signals used and the CRQ ids compared;
   - which features switch to the new method (history rows, approval timing, platform pattern, Create
     suggestions, overlap check, service rule files) and which keep product;
   - rename the "Service" label to "Product" wherever it means the product.
7. Guardrails: history never changes score, status or rule-set id; no people stored; no new Remedy
   requests; proof plan for Phase 1 (identical scores and findings on all 6,461 + 16 reviews; only history
   sections may change, with a before/after count of each note type).
Then stop for my decisions.