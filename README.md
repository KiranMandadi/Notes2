Update the git rules in .github/copilot-instructions.md. Replace the rule "If the user pastes git commands … do not run them" (and any rule that forbids all git operations) with this section, verbatim:

## Git operations
- Never run git on your own initiative. Read-only git (status, diff, log, show) is always allowed.
- Run git add / commit / push only when the user explicitly asks in that message (e.g. "commit and push", or pastes the commands and says to run them).
- Before committing: run `git status` and show the list of files. Stop and ask if any of these appear: .env, history.db, anything under work/, reports/ or logs/, or any file the current task didn't touch.
- Stage files by name (`git add <files>`), never `git add -A` or `git add .`.
- Use the commit message exactly as the user gives it. If none is given, propose one and wait for approval. Never add a "Co-authored-by" or any other trailer.
- Push only to origin on the current branch. Never force-push, rebase, amend a pushed commit, reset, or delete anything.
- Never create branches or tags unless the user asks for that specific branch or tag.
- After pushing, report the commit hash and the files included; nothing else.

Make only this edit and show me the diff. Don't run any git commands now.