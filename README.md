In profiles/enterprise/config/reports.yaml set pending_cache_minutes: 0 (no shared Pending result;
every visit and Refresh reads Remedy live). Keep the parallel reads and the one-read-at-a-time
behaviour for simultaneous visitors only if it doesn't reuse a finished result. Update docs and
decisions.md ("shared mode serves live Remedy data; no cached results"). Re-record the baseline.
Run python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.