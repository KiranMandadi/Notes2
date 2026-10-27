Phase B - apply the pre-publish clean-up. No change to rules, scoring, report content or behaviour.

APPLY (from the audit):
1. Replace the 167 real change numbers in the 10 files with clearly synthetic ids
   (e.g. CRQ000000000001...) or wording; none may be a real change number.
2. .env.example: keep it (edit, never delete). Every key the tool needs, example values only
   (e.g. https://remedy.example.com), a short comment per key; remove CHANGELENS_ALLOW_SAMPLE_DATA,
   REMEDY_MOCK_DATA and the sample/mock comments.
3. tests/test_security.py: use documentation IPs (192.0.2.x, 198.51.100.x) instead of this Mac's.
4. python scripts/check.py passes on a fresh clone with no Remedy settings (it sets placeholder
   values for its own run only).
5. README quick start: prerequisites with a Python 3.11+ check (macOS: python3 may be 3.9);
   macOS, Windows and Linux; cp .env.example .env (Windows: copy); crq login run by the user;
   history load step; crq ui --local for personal use; shared mode only on the serving machine
   with the read-only account.
7. Move the 8 built plans in docs/plans/ to docs/archive/; update INDEX.md, docs/README.md and
   every reference (pack source: fields too, with pack version bumps).
9. Fix the contracts.md error example (real code CR_NOT_FOUND), the README field_map claim, the
   open-items line numbers and D9's order; document extensions and organizations.
10. Remove FREEZE_STATES (cr_core/quality/calendar.py). Leave serve_forms and reads_people.
11. (covered in 5)
12. Remove docs/design/ from the repo (I keep a local copy) and any references to it.
13. .gitignore: add *.db-journal and .mypy_cache.
KEEP: Confluence page ids, the company name (D4), LICENSE.

ALSO:
a. .vscode/: keep only shared, path-free files (e.g. extensions.json); ignore the rest.
b. .github/workflows: list each workflow, its trigger, and whether it needs secrets, network or
   Remedy; make them pass on a fresh clone with no Remedy settings, or disable them until the
   org's Actions policy is known.
c. CODEOWNERS: replace the @your-org placeholders with a single "* @<HANDLE>" line (I will give
   the handle; leave <HANDLE> and tell me); keep the team layout in docs as D3.
d. Scan .github/agents/ and .github/ISSUE_TEMPLATE/ like the docs.
e. docs/README.md lists every doc with one line saying what it is for.
f. Confirm history.db and its -wal/-shm files live under an ignored path.

VERIFY:
- Re-run the sensitive-data scan on the whole tree: report 0 real change numbers, 0 real hosts,
  0 real IPs, 0 personal paths.
- Findings, scores and statuses identical on 6,461 past + 16 pending.
- python scripts/check.py --browser passes; fresh-clone test passes following only the README.

THEN give me (don't run) the exact git commands to: delete refs/agents/* and tag v0.8.1 locally,
review git status (nothing from work/, history.db*, .env, reports/, logs/, .venv), commit, and push
main only (git push origin main - no --mirror, --all or --tags).
List files changed/removed/moved. No branches, tags or commits yourself.