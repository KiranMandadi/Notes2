   git status --short
   git add -A
   git diff --cached --name-only | grep -E '^(work|reports|logs|\.venv)/|history\.db|(^|/)\.env$'
   git commit -m "0.26.0: accuracy audit fixes - Standard changes, safety pattern, reason sentences, word counts, scheduler names, CI types, one weight per rule; certifi upgrade; permanent audit check"
   git push origin main



Step 2 - measure only: proposal 8 ("Please confirm", 0 points) on top of the step-1 rules, for the
rules listed, only where the verifier finds the item in the owner's other fields and nothing can
settle it. The note must name where it was found, e.g. "A deployment tool is named in the Backout
plan - please confirm it applies to the implementation." Exclude MF-01 and GEN-01. Report counts
per rule, status changes, pending ids, and 5 example ids per rule (work/ only). Then stop.