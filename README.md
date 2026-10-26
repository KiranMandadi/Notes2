Bug in 0.21.0 (Q-COMPLETE-07): on 2455359 it reports 3a-3c and 4a-4b as missing, but the Notes
answer them, written as "3. <question>" followed by "a. While change is being performed: ...",
"b. During Market Open: ...", "c. The next business day: ..." (and "4." with "a." / "b."). The
parser must recognise sub-questions written as "a." / "a)" / "(a)" / "3a" / "3.a" under their parent
number, and question numbers with or without a trailing "." or ")".
1. Fix the parser; add tests for each of these formats, using 2455359's layout (synthetic text).
2. Re-measure: of the 248 past + 3 pending findings added in 0.21.0, how many disappear with the
   fixed parser, and how many "missing" findings remain (counts only). Also how many existing
   "unanswered"/"N/A" findings change.
3. List 5 past CRQ ids that still have a "missing" finding after the fix, so I can check them in
   Remedy.
Until I confirm, a "missing" finding must only be raised when the parent question number itself is
absent, or the part's label is clearly absent; if the parser can't tell, don't raise it.
Proof from an actual re-run: only Q-COMPLETE-07 changes. Run python scripts/check.py --browser;
list files changed; stop. No branches, tags or commits.