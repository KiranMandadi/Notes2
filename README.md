git config user.name
git config user.email
git remote -v

git for-each-ref --format='%(refname)' refs/agents/ | xargs -n 1 git update-ref -d
git tag -d v0.8.1
git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'


git commit -m "ChangeLens 0.21.11: report and Rules page redesign, rule accuracy fixes, freeze calendar, shared mode, documentation and pre-publish clean-up"
git push origin main


git clone <repo url> cl-test && cd cl-test
python3.12 -m venv .venv && source .venv/bin/activate
pip install -r requirements-dev.lock && pip install --no-deps -e .
cp .env.example .env
python scripts/check.py