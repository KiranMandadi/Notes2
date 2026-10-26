Shared mode for the Console (permanent, configurable). Plan first, then STOP for my OK.

Goal: other people on the network open http://<my-ip>:<port>/ with no token and use it at the same
time. This must be the default for everyone running the enterprise profile, set in config, not a
one-off flag.

Design to propose in docs/plans/shared-mode.md (no code yet):
1. Config (enterprise profile, e.g. config/console.yaml): mode: shared | local (default shared),
   bind_host (default 0.0.0.0), port (fixed, default 8765), access_log: true. `crq ui` reads it;
   a CLI flag may override for local testing. Print the shareable URL(s) on start (LAN IPs).
2. Shared mode removes: the ?t= session token and cookie, localhost-only binding, Host/Origin
   checks. Local mode keeps today's behaviour exactly.
3. Shared mode keeps, always: creating is disabled regardless of REMEDY_ALLOW_CREATE (Create
   screens hidden, create API returns CREATE_DISABLED); escaping of all change/Jira text; CSP
   'self' only; no external requests; credentials never sent to the browser, logged or shown.
4. Remedy access: one server-side sign-in (the configured read-only account), token in memory,
   shared across users; refresh safely when it expires; never per-user credentials in the page.
5. Multiple users at once: threaded server; per-request state only (no global "current change");
   thread-safe caches and history DB access (read-only connections); a Remedy concurrency limit
   (e.g. 4 in flight) with BUSY when exceeded; a slow request must not block others.
6. Access log (append-only, git-ignored, rotated): time, client IP, page/API, CRQ id, status code,
   duration. Never field values, change text or credentials.
7. Simple rate limit per client IP (e.g. 60 requests/min) returning RATE_LIMITED.
8. Landing page/footer: no wording that implies "only on this computer".
List files to change, tests to add (two clients in parallel; no token needed in shared mode;
create always refused in shared mode; local mode unchanged incl. token checks; log contains no
change text), docs to update (user guide "Sharing the Console", configuration, security notes),
and any new dependency (none expected - ask me first).
No branches, tags or commits.