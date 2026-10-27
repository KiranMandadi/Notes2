Fix all 70 (wrong, outdated, unclear, terminology), docs only except as noted. Decisions:
1. Terminology: "restricted period" for the periods everywhere (docs, profiles/README, CC-05 title
   and why in change-class.yaml); keep "Freeze clash", "Freeze calendar", "freeze exception".
   Rule-set id may change; findings, scores, statuses must not.
2. Create screen: describe it as switched off in every mode (ENABLE_CREATE = False); only
   crq create creates. Keep the sections, marked "switched off - groundwork for a later release".
   Remove "Console writes crq-create.log / drafts" claims. docs/README.md: drop Create, add Rules page.
3. History schema: make docs/history-schema.md match what the loader creates (v3). If the SQL
   script is stale, update it to build the identical v3 schema and add a test that compares it with
   the loader's schema; if nothing uses it, tell me and I'll decide on removal.
4. History Refresh agent: use 4 weeks, as crq-load refresh does.
5. docs/quality-rules-v2.md: fix the "wrong" rows; add a banner "Original design spec - current
   behaviour is in rules-authoring.md and rules-catalogue.md". Do not move it.
6. Items that depend on cr_core/config.py or cr_core/history/config.py: list the exact questions
   (file, setting, what to look for) and stop on those; I will check them by hand.
After fixing: re-run this accuracy check (expect 0 wrong/outdated except the config.py items),
check every link, and prove findings, scores and statuses identical on 6,461 + 16. Run
python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.