Console start-up, UI/launch only:
1. Open the browser at http://localhost:<port>/ (not the host name). Print addresses as:
   "This computer: http://localhost:<port>/" then "To share: http://<ip>:<port>/" for each address.
   List the host name only if it resolves to one of this machine's addresses. Host check keeps
   accepting localhost, 127.0.0.1, the IPs and a resolving host name.
2. Busy port: in shared mode do NOT switch ports; exit with a clear message ("Port 8765 is already in
   use - possibly another ChangeLens Console. Stop it, or start with --port <n>.") and a non-zero
   exit code. In --local mode keep today's behaviour (pick a free port). Tell me what each mode does
   today first.
Tests for both. Run python scripts/check.py --browser; list files changed; stop. No branches, tags
or commits.