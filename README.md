Add a diagnostic command `crq timing <CRQ>` (read-only, live): run one report and print time per stage
- sign-in, each Remedy request (form, rows, seconds, new connection or reused), rule scoring, history
comparison, overlap search, rendering. Also print: Python version, OS, history.db path type
(local/network) and size; whether a proxy is in use (urllib getproxies, incl. Windows registry) and
for the Remedy host; DNS lookup time and the address family used (IPv4/IPv6) for each new connection;
TLS handshake time; total new connections vs requests. Codes and timings only, no change text.
Document in operations.md. Run python scripts/check.py; list files changed; stop. No branches, tags or
commits.


git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Add crq timing diagnostic: per-stage and per-request timings, connection reuse, proxy, DNS/IPv6, TLS"
git push origin main


git pull origin main
.venv\Scripts\Activate.ps1
python -m pip install --no-deps -e .
crq --version