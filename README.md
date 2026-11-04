Add `crq ui --stop` and `crq ui --restart` (macOS, Windows, Linux):
1. On start, the Console writes work/console/<port>.json (pid, port, mode, version, start time, random
   secret), git-ignored, owner-only permissions; removed on clean shutdown.
2. Local-only POST /api/shutdown (127.0.0.1/::1 only, requires the secret, never reachable from other
   machines, not listed in the UI); finishes in-flight requests briefly, then exits.
3. --stop: read the control file, call shutdown, wait until the port is free (timeout 15 s), report
   the result. No control file / process gone: "No ChangeLens Console running on <port>". Port held by
   a non-ChangeLens process: refuse and name it - never kill it.
4. --restart: --stop, then start with the same mode and port (or the flags given).
5. Never stop another user's Console; no force-kill unless --force and the pid matches the control file.
6. Docs: operations.md and README - update steps become: git pull -> pip install --no-deps -e . ->
   crq ui --restart; note that a Console run as a Windows Scheduled Task is restarted with schtasks
   /End and /Run instead.
7. Must work the same on macOS, Windows and Linux with the standard library only (no psutil or new
   dependencies): owner-only file permissions per OS, process-alive check per OS, best-effort naming
   of a foreign port holder (lsof / netstat+tasklist), never required.
Tests: stop, restart, stale control file, foreign process on the port, shutdown refused from a
non-local address and without the secret. Run them on this Mac and tell me the exact commands to
verify on the Windows VM. Exclude cr_core/config.py and cr_core/history/config.py from every search.
Run python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.


git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "crq ui --stop and --restart: safe local shutdown via control file, cross-platform"
git push origin main


Then on the VM, in PowerShell, update this one time the manual way:

# stop the running Console first (Ctrl+C in its window, or schtasks /End)
git pull origin main
.venv\Scripts\Activate.ps1
python -m pip install --no-deps -e .
crq ui

From the next update onward, the VM steps become:

git pull origin main
python -m pip install --no-deps -e .
crq ui --restart