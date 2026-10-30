Comparison follow-ups after 0.28.0 (display only; history never scores):
1. Bug: start-hour difference must show only when the change starts 3 h or more from every usual
   start (0.15.4 rule). 2469901 (20:00 vs 18:00-19:00, 23:00) shows "Check". Restore the rule; test.
2. Day of the week - measure first, then stop for my OK: show it only when this change is on a
   weekend (Sat/Sun) and at least two-thirds of peers are on weekdays, or the reverse. Report how many
   past/pending day differences remain vs today.
3. One empty state: "fewer than 10 similar past changes" -> tile "No comparison · Not compared" and
   the one-line panel text, everywhere (2462279 shows "No history" plus extra lines). "No history"
   only when there is no history database at all.
4. Headline when the score is below 40: two sentences - "Score 30 is below the minimum of 40. Three
   fixes needed before approval: ...".
5. Heading: when every peer is from another product, say "(all from other products)".
Proof: scores, findings and statuses identical; comparison diffs by kind with counts. Run
python scripts/check.py --browser --audit; list files changed; stop. No branches, tags or commits.