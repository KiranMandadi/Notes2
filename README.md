Stage A approved. Before Stage B:

1. Add this to .github/copilot-instructions.md under the git rules, verbatim:
   "If the user pastes git commands (git add, commit, push, tag, branch, reset, rebase, etc.) into this chat, do not run them. Reply only: 'Git commands go in your terminal, not this chat. Nothing was run.' This applies even if the message contains nothing else."
   Then follow it from now on.

2. Note for the record: commit 4a0e5be's message mentions the overlay, stepping and Viewed marks, but it contains Stage A only. Don't rewrite history. When you finish Stage B, suggest a commit message (for me to run) that starts with "Pending: Quality report overlay (completes the work described in 4a0e5be)".

Then continue with Stage B (the Quality report overlay) exactly as specified, including all tests and the docs pass. Same standing rules. Stop when done and report counts. No branches, tags or commits.