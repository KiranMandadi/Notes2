Finish the ORR spike, read-only. Same standing rules: no git operations; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; never run crq login; GET requests only; codes, field IDs, scale words and counts only in replies.

Context: the risk report shows three different things. (a) the ORR rating on Schwab's scale, e.g. "4 = Very High", shown as text in the CI Name / Field Value column; (b) that factor's risk value on the 1–5 scale, e.g. 5, which field 880001551 holds; (c) the Aggregate Risk Value, e.g. 3, which becomes the change's Risk Level. We will display (a), never (b) as "ORR".

1. Read CHG:ChangeRiskDerivedTemplateSelectionDerivedFactorsLookup ONCE, narrowly filtered to the "Maximum Application Priority/ORR Rating" factor (retry once on failure). Report the full ORR scale (number and word for every level) and the risk value each level maps to.
2. State whether the mapping is one-to-one (each risk value comes from exactly one ORR level).
   - If yes: the ORR label can be derived from field 880001551 with no extra request.
   - If no: the ORR label must come from the derived-factors row's Field Value (400009800) on CHG:ChangeRiskDerivedFactors, 1 extra request per change. Describe how to parse it safely (number before "=", word after) and how often it fails to parse on the 73 pending changes.
3. On the 73 pending changes: distribution of field 880001551 values (count per value, count empty); distribution of ORR labels from the derived-factors rows; and the number of changes where the two disagree under the mapping.
4. Aggregate check: on the 73, recompute the Aggregate Risk Value from the derived-factor rows (risk value × weight) and compare it with the change's Risk Level (1000000180). Report the formula that matches (plain average? weighted? rounding rule?) and the match count. Also count the changes where ORR is the top level (e.g. Very High) but Risk Level is 3 or lower.
5. Add all of this to docs/research/orr-rating.md under "ORR scale and mapping — to be confirmed by Kiran/Remedy team". No config changes.
6. Explain why the skipped test count is now 31 (it was 28): list the 3 newly skipped tests and why they skip.

Report counts only. No branches, tags or commits.