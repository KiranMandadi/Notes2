Docs tidy - docs only, no code:
1. history.md, history-schema.md, loader.md: propose merge into one history.md (use, load, schema)
   or keep separate with a one-line purpose at the top of each; show which, then apply.
2. roadmap.md: bring up to date with 0.20-0.27 (local rules, Pending filters/sort/search, research,
   accuracy audit) or merge into open-items.md if it only repeats it.
3. Create docs/decisions.md: product decisions from this project, one line each with date, grouped
   by area (UI, rules, scoring, security/sharing, history, research/audit).
4. docs/research/*: add a header line "Date - status (e.g. findings applied in 0.27.x)" to each.
5. docs/README.md lists every doc with a one-line purpose; check every link.
6. Check .github/copilot-instructions.md has the standing rules (no commits/pushes unless I ask in the
   terminal; never crq login; codes and counts only; proof on all past + pending for rule changes).
Run python scripts/check.py; list files changed; stop. No branches, tags or commits.