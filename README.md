README.md polish - wording and structure only; every fact must stay accurate (re-check after).
1. Replace the opening (lines 1-16) with: title; tagline "Quality checks for BMC Remedy changes,
   before they reach approval."; one paragraph: reads a change from Remedy, checks it against the
   agreed change-quality rules, shows in seconds Ready / Needs work / Blocked with each issue and its
   fix; who uses it (developers, reviewers and approvers, directors); read-only, never changes a
   change. Keep "This repository holds configuration, never change data..." as the next paragraph.
2. Add "## Three ways to use it": Report Console (crq ui, in the browser, for everyone) - crq
   command (engineers, scripts) - Copilot agents (VS Code). One line each with a link. Move the
   agents table under "## Using the agents in Copilot Chat".
3. Prose says "product" not "service" (keep the --service flag and config key names).
4. Console create: "is switched off; it may be enabled in a later release" (no promise). Change
   Creator row: add "(creating is off by default - see Setting up)".
5. Next to Ready / Needs work / Blocked, one line: "Score weights and thresholds are ChangeLens
   defaults, pending confirmation with the Change Management office."
6. Keep the command table; move the per-command explanation bullets (current lines 200-210) to
   docs/user-guide.md (or contracts.md) and link to them.
7. Add "## Getting help": owner (see .github/CODEOWNERS), raise a problem or rule change with the
   issue template, open work in docs/open-items.md.
8. Optional: generate docs/images/quality-report.png from a synthetic test fixture only (no real
   data; run the sensitive-data scan on it) and show it under the opening. Ask me before adding it.
Then re-run the accuracy check on README.md and docs/user-guide.md, check links, run
python scripts/check.py, list files changed, stop. No branches, tags or commits.