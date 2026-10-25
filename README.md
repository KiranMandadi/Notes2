Performance: the "Comparing with past changes" step takes 10-15 s per report (it was ~1 s with 5,000
changes). Goal: much faster with ZERO change to any output. Phase 0 = measure and propose only; write
docs/plans/performance.md and stop. No profile changes; no branches, tags or commits; no new dependencies.

1. Profile one report end to end on 3 pending changes (e.g. with cProfile or timing around each step):
   time for Remedy reads vs each history step (window comparison, approval timing, track record,
   "last time this change ran" similarity, service pattern for platform identification, rule evaluation,
   rendering). Report the top 10 hotspots with times and query counts.
2. Check: SQLite indexes for every column used in WHERE/JOIN/ORDER BY (including schema v3 columns and
   tasks); repeated queries for the same rows (N+1 patterns); the database opened more than once per
   report; work that doesn't depend on the change and could be computed once (service patterns, medians,
   percentiles); text similarity running on all candidates without a cheap pre-filter.
3. Propose fixes, only ones that cannot change results, e.g.:
   - missing indexes (added by the loader/schema, applied on upgrade);
   - one read-only connection per Console process;
   - an in-memory cache of per-service history aggregates, keyed on the history database file's
     modification time and size so it refreshes automatically after a reload;
   - fetching a service's past changes and their child rows in one query each;
   - a cheap exact pre-filter before the similarity score (only if it provably cannot drop a candidate
     that would score >= the threshold);
   - computing the service platform pattern once per service per database version.
   Do NOT parallelise Remedy calls (rate limits) and do not change any threshold, rule or wording.
4. For each fix: expected gain, risk, and how equality is proven.
Proof required for Phase 1: every review of all 6,461 past + 16 pending changes byte-identical before and
after (status, score, findings, history sections), plus report HTML identical except timing; and a timing
table before/after per step. Then stop for my OK.