Research only - change no tool code, rules or packs. Work in work/research/ (git-ignored); write the
summary to docs/research/history-rule-discovery.md with counts and rule codes only - no change text,
no names, no CRQ ids in the doc (ids only in the work/ files). Read-only history.db; no Remedy calls.

PHASE 0 - outcome data (then STOP and report):
- Which outcome signals exist in history.db per change: closure status (Successful / Backed Out /
  Failed / Cancelled), linked incidents within N days, reschedules or window changes, follow-up
  Emergency changes on the same product. Counts per signal; how complete each is; date range.
- Propose a "bad outcome" label from what exists, with counts.

PHASE 1 - do today's rules predict outcomes? For every rule: bad-outcome rate when it fired vs not,
ratio, counts, and the same within each risk level. Older changes vs the most recent quarter
separately. Flag rules with no signal, and rules with strong signal.

PHASE 2 - candidate patterns (deterministic, explainable only): field and Work Detail presence,
task names/counts, CI links, text sections/keywords in Notes/Backout/Implementation plan, lead
time, window length/day/hour, reschedules, approval timing, risk vs impact mismatch, and per product
and coordinator group. Keep patterns with >= 50 changes and a clear rate difference that also holds
in the most recent quarter and within risk levels.

PHASE 3 - report: top 10-15 candidates, each as an evidence card: plain-language rule ("A change that
... "), scope (global / group / product), counts and ratios, recent-quarter check, which existing
rule it overlaps with, a suggested severity, and 5 example CRQ ids (work/ file only).
Stop after each phase for my OK. No branches, tags or commits.