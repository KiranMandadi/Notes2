History for other users (docs + folder only; no code changes):
1. Track an empty folder work/history/enterprise/ with a .gitkeep. .gitignore must keep ignoring
   everything else under work/ - add only the negations needed for that one .gitkeep, and confirm
   history.db, history.db-wal, history.db-shm and any other file there stay ignored
   (git check-ignore -v on each).
2. README Quick start, step 5 "History (optional)", reword as two options:
   a) Use the shared copy (recommended): copy history.db from the team's shared location
      (<SHARED_HISTORY_LOCATION> - placeholder, I will fill it in) to
      work/history/enterprise/history.db. Copy only history.db (no -wal/-shm files), after the
      weekly refresh has finished. ChangeLens finds it there automatically; alternatively set
      CHANGELENS_HISTORY_DB to its path. Then run crq history status.
   b) Load your own with crq-load (the current steps), only if you maintain the shared copy.
   Add one line: without history, reports still give the full verdict; only the comparison with
   past changes and the suggestions are missing.
3. Same wording in docs/setup-enterprise.md and docs/history.md. State clearly: never commit
   history.db or share it outside the approved location; it holds no names but does hold change
   text.
4. Add an open item: "Set <SHARED_HISTORY_LOCATION> and who refreshes the shared copy weekly."
Run python scripts/check.py; list files changed; stop. No commits, branches or tags.