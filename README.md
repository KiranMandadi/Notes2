Approved - implement all three:
1. Both parts: (a) evict pooled connections idle longer than a conservative threshold (setting,
   default 15 s) before handing them out; (b) on a reused connection, first attempt gets a short read
   timeout (setting, default 5 s) and on failure retries once immediately on a guaranteed-fresh
   connection with the normal timeout - GET/idempotent only; create keeps today's rule (retry only if
   nothing was sent). No backoff sleep before that fresh-connection retry.
2. Sign-in: apply the same fast-fail + fresh retry inside the sign-in call so the token lock is held
   only briefly.
3. logs/crq-ui.log: for any report or Pending load over 5 s, one codes-only line with stage timings,
   slowest request, new/reused, stale evicted, fast-retries, timeouts (no change text, no token).
Also add the glob exclusions for cr_core/config.py and cr_core/history/config.py to every search you
run (it was matched again).
Proof: results identical on all past + pending; crq timing --repeat 15 before/after (I'll run both on
Mac and VM). Run python scripts/check.py --browser --audit; list files changed; stop. No branches, tags
or commits.

git add -A
git status --short
git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
git commit -m "Connection reliability: evict idle pooled connections, fast-fail and fresh retry on reused connections, fast sign-in, slow-report logging, crq timing --repeat"
git push origin main