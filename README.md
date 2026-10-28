Drafts and MF-03: on a mainframe draft with no categorization tier and no Package ID, MF-03 gives a
"Please confirm" note (0 points): "If this change promotes a package, name the promotion tool and
package (for example a ChangeMan or Endevor package)." When a draft has a tier or Package ID, the
scoped rule applies as for changes. Live changes unchanged. Tests; proof: findings, scores and
statuses on all past + pending identical to 0.24.0. Run python scripts/check.py; list files changed;
stop. No branches, tags or commits.

   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.24.0: MF-03 scoped to package promotions, MF-02 widened; CC-08 advisory; history research"
   git push origin main