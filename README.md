Make every file under profiles/ tracked, then stop before committing.
1. Show which .gitignore rule(s) ignore files under profiles/ (git check-ignore -v) and list the
   ignored files (paths only).
2. Fix .gitignore so nothing under profiles/ is ignored (remove or narrow the pattern, or add
   "!profiles/**" after it). Keep ignoring work/, history.db*, .env, reports/, logs/, .venv/.
3. Run the sensitive-data scan on every file under profiles/ (real change numbers, company hosts,
   internal URLs, IPs, personal paths, people's names, passwords/tokens). Company name and
   Confluence page ids are allowed (D4). Report counts; if anything is found, list file:line and
   stop.
4. git add profiles/ .gitignore; show git status --short for profiles/; confirm
   git ls-files profiles/ | wc -l equals find profiles -type f | wc -l.
5. Run python scripts/check.py and the baseline check (enterprise.sha256 must match).
Do not commit or push. No branches or tags.