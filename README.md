Automated accuracy audit - no human labelling; Remedy data and code are the source of truth.
Report first, change nothing until I OK. Doc: docs/research/accuracy-audit.md (counts and codes
only); details and ids in work/accuracy-audit/ (git-ignored). Read-only Remedy/history.

1. Independent verifier (separate code from the rules, deliberately broader matching): for every
   finding on all 56 pending and all 6,461 past changes:
   - "not found / missing" findings: search ALL text fields, Work Details and task names, case-
     and format-insensitive, for what the rule says is missing; if found -> "suspected false".
   - value findings (risk, impact, urgency, dates, durations, lead time, freeze, overlaps, CI
     counts): recompute from raw Remedy fields and compare with the report -> "mismatch".
   Report per rule: findings checked, suspected false, mismatches, with 10 example ids each.
2. Consistency: per rule fire rate by template version, platform, coordinator group and month;
   flag sharp differences. Find contradictions inside a report (finding vs At a glance, evidence
   vs message, brief vs Quality report).
3. Code review of cr_core/quality, template parsing, labels, calendar, history comparison:
   exact-wording matches, position/order assumptions, case/whitespace/Unicode/bold, empty vs
   missing, time-zone/date edges, silent fallbacks, regex over/under-match. Rank High/Med/Low with
   affected rule codes.
4. Stress test plan: list the Notes formats seen in history and the synthetic cases to add.
5. Dependencies: each package, pinned version, any unpinned or with known issues.
6. Proposal: for each rule with suspected false findings, the fix (with measured effect), or a
   "Please confirm" (0 points) fallback where the verifier and rule disagree and it can't be
   resolved.
Stop with a ranked list, highest false-alarm risk first. No branches, tags or commits.