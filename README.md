Shared mode for the Console - build it (plan: docs/plans/shared-mode.md). Decisions:
S1 yes - build as described in sections 3-10.
S2 (a): shared by default in the enterprise profile; allowed_networks stays as a setting but empty
   = anyone who can reach the port; no refusal to start. crq ui --local still forces today's
   behaviour (token, 127.0.0.1).
S3 keep both: a POST's Origin must equal http:// + its own Host; Host checked against
   allowed_hosts, default this machine's host names and IPs with the port.
S4 yes: docs/operations.md states the shared server runs under the dedicated read-only Remedy
   account in its .env, never a personal login.
S5 Recent reports: only the visitor's own (by IP, this run).
S6 port 8765, remedy_concurrency 4. S7 reuse UI_BUSY (503 + Retry-After). S8 client IP in the access
   log in both modes. S9 rate limit counts API and report requests only.
Always, in both modes: creating refused in shared mode (CREATE_DISABLED, no Create tab) whatever
REMEDY_ALLOW_CREATE says; all change/Jira text escaped; CSP 'self'; no external requests;
credentials and tokens never sent to a browser, logged or shown; access log never holds field
values, change text, query strings or cookies.
Update the docs listed in section 10 (user guide "Sharing the Console", configuration, SECURITY.md,
operations, architecture, contracts, setup-enterprise, README, copilot-instructions wording,
CHANGELOG, minor version). No new dependencies.
Proof: local mode unchanged (all existing tests pass); the new section 10 tests pass (no token in
shared mode, two clients in parallel, create always refused, Host/Origin, rate limit, log hygiene,
token refresh, config); re-record the enterprise baseline; run python scripts/check.py --browser;
list files changed; then stop. No branches, tags or commits.