Check only: search the repo (.github/agents, prompts, scripts, docs, tests) for any reader of the
catalogue/validate JSON that still uses "services" or counts.services. List file:line; fix any to
"local"; note the rename in CHANGELOG under "Changed (JSON)". Run python scripts/check.py; list
files changed; stop. No branches, tags or commits.