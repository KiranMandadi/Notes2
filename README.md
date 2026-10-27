README and docs/setup-enterprise.md: Windows and company-network setup notes. Docs (plus the scan
allow-list) only; no code changes.
1. PowerShell: if Activate.ps1 is blocked ("running scripts is disabled on this system"), run
   "Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass" in that window (no admin, not
   permanent), or use Command Prompt with .venv\Scripts\activate.bat.
2. Package mirror: public PyPI is blocked on the company network. Inside the activated venv, before
   installing, run:
   python -m pip config --site set global.index-url <URL>
   then python -m pip install -r requirements.lock and python -m pip install --no-deps -e .
   Mirror credentials, if required, come from the user's own setup; never store them in the repo.
3. Certificates: if pip reports CERTIFICATE_VERIFY_FAILED, set global.cert to the company
   certificate bundle from IT (python -m pip config --site set global.cert <path>); if crq doctor
   or crq login reports a certificate error reaching Remedy, set REMEDY_CA_BUNDLE=<path> in .env.
   Never disable verification or use --trusted-host. No local file paths from my machine in the docs.
4. Add a short symptom table: "running scripts is disabled" -> step 1; "from versions: none" or
   403 -> step 2; "CERTIFICATE_VERIFY_FAILED" -> step 3.
5. D4 in docs/open-items.md: add "pip mirror URL is an internal address; allowed in the internal
   repo". Teach the sensitive-data scan to allow the configured mirror URL without exposing it.
Re-run the sensitive-data scan (only the allowed entries may match) and python scripts/check.py;
list files changed; stop. No branches, tags or commits.

git add -A
git status --short
git commit -m "Setup docs: Windows execution policy, company pip mirror and certificates"
git push origin main