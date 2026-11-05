git status
git add -A
git commit -m "Pending 0.41.0: executive view (approver display name, View by tabs, column sort, Today/Tomorrow and freeze tags, sticky header, fallback to all approvers)"
git push


cd C:\CodeBase\changelens
crq ui --stop
git pull
pip install -e .
crq ui