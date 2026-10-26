Decisions:
1. Redaction: yes - move the masking patterns to cr_core/history, loader imports them; apply to the
   current change before comparing. Display only.
2. GEN-02: (a), extended - any non-empty Deployment_Strategy pick-list value satisfies GEN-02
   (normalise "Blue/Green" etc.; Big Bang and Feature Flag count too). Keep the existing message for
   when nothing is stated; drop my "Its deployment strategy is..." wording. Add to D10: "Is a
   strategy pick-list value enough for GEN-02, or must the tool/pipeline be named?"
3. Overlaps: compare every pair within the gap; label "Overlaps (same product)".
4. MF-05 message: name the online-day part the window runs into, e.g. "The window runs into the
   mainframe online day (Fri 07:00-19:00)."
Before applying 2 and 3: measure in memory and report counts only (GEN-02 findings removed past/
pending, score and status changes; overlaps added/removed past/pending). Then stop for my OK.
After OK: apply these plus the rest of part B as listed; proof from an actual re-run; run python
scripts/check.py --browser; list files changed; stop. No branches, tags or commits.