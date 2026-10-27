Pre-publish clean-up (docs, hygiene, dead code). No change to rules, scoring, report content or
behaviour. Work in two phases.

PHASE A - audit only, change no files. Report as tables (paths, codes, counts; never values or
change text):
1. Sensitive data in tracked files AND git history: real CRQ/INC numbers, people's names, internal
   URLs/hosts (Jira, Remedy), IPs, machine names, tokens, passwords, quoted Notes text. Tests and
   docs must use synthetic data only.
2. .gitignore coverage: work/, history.db*, .env, reports/, logs/, drafts, caches; is anything
   ignored currently tracked? Is there a .env.example with no values?
3. Dead or obsolete: unused modules/functions, settings, flags, scripts, templates, sample-profile
   or old Create leftovers, stale TODO/FIXME. For each: evidence it is unused (no import, no test,
   no reference) and a keep/remove recommendation.
4. Docs vs code: every command, setting, file path and version mentioned in *.md exists and is
   current; broken internal links; outdated sections (pre-0.15 behaviour, removed features);
   duplicated content across README, user guide, contracts, rules-authoring, configuration,
   copilot-instructions; plans that are done and should move to docs/archive/ (update INDEX.md).
5. docs/open-items.md accurate for today (closed items marked, D18-D24 present, counts right).
6. Repo hygiene: README quick start for a new user (prerequisites, install, .env, crq login done by
   the user, history load, crq ui, shared vs --local), CODEOWNERS, licence/internal-use notice,
   CHANGELOG consistent with pyproject version.
7. Fresh-clone test: clone to an empty temp folder, follow only the README with the sample-free
   enterprise profile and a mocked Remedy; list every step that fails or is missing.
Then STOP with a prioritised list (must fix before publish / should fix / nice to have).

PHASE B (after my OK): apply only what I approve. Proof: findings, scores and statuses identical on
6,461 past + 16 pending; python scripts/check.py --browser passes; fresh-clone test passes. List
files changed/removed/moved. No branches, tags or commits.