Decisions on docs/plans/performance.md: P1 yes (fixes 1-4). P2 yes (fix 5). P3 yes - the Remedy
sign-in token is kept in memory only, never written to disk or logs, cleared when the Console stops,
and re-obtained automatically if Remedy rejects it. P4 yes - the banner shows real progress:
"Reading the change from Remedy..." then "Applying the rules..." (only steps that actually happen).
P5 yes - delete work/perf/ after Phase 1 and confirm.
Build Phase 1, prove byte-identical review and report data for all 6,461 past + 16 pending changes
(HTML identical except generated time), show the before/after timing table (3 live runs each) and
request counts, run python scripts/check.py --browser, and stop. No branches, tags or commits.