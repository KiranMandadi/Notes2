Accuracy bug - check and measure first, change nothing until I OK.
Case: CRQ000002474250. Q-COMPLETE-07 says 3a-3c, 4a-4b and 5 are missing, but the Notes answer them.
This change uses a different template version: header "Questions 1-5 | 6-8 for RL4/5 Only";
Q3 "What are the potential business or service impacts?" (a/b/c), Q4 "If a problem is discovered
during market hours or the business day, what would the impact be?" (a/b), Q5 "What happens if the
change is not approved?". Q-VAGUE-01 also fired (Major) though the text says "No business or service
impact is expected because these jobs are not active yet" and "No impact ... for the same reason".
1. Explain exactly why each fired (which pattern/wording the rule expects; codes only, no text).
2. Inventory template versions in history: distinct header lines and question-wording variants,
   with counts and date ranges (counts only in the doc; examples in work/).
3. Proposed fix for Q-COMPLETE-07: match questions by number/sub-letter and position, wording only
   as a fallback; support every template version found; required set per version (6-8 vs 6-9 at
   risk 4-5); "missing" only when the number is absent; present-but-reworded counts as present.
4. Proposed fix for Q-VAGUE-01/03: accept a reason introduced by because/since/as/due to/so in the
   same sentence, and "for the same reason" / "same as above" when a preceding answer in the same
   question gave a reason.
5. Measure both in memory on all past + pending: findings removed/added per rule, score and status
   changes, pending ids affected. List 10 past ids per rule whose finding disappears and 5 where a
   finding remains, so I can read them in Remedy.
Then stop. No branches, tags or commits.