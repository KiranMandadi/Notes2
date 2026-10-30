Add to .github/copilot-instructions.md under working rules: "Never read, search or print
cr_core/config.py or cr_core/history/config.py - exclude them explicitly from every grep/rg/find
(e.g. --glob '!cr_core/config.py' --glob '!cr_core/history/config.py')." Docs only; list files
changed; stop. No branches, tags or commits.

   git add -A
   git status --short
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.29.0: parallel Remedy reads, shared Pending result (10 min), sticky header, Back to top"
   git push origin main