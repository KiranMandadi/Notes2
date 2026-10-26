Quality report summary block, UI only - go back to ONE card (as before the two-card change):
1. Inside the card, split at the same position as the Issues to fix / At a glance column boundary
   below: left part = verdict chip, next-action headline, subtitle (same width as Issues to fix);
   right part = Blockers · Major · Minor (same width as At a glance).
2. Count cells: the previous inset tinted-box style, three equal cells within the right part,
   number above label, vertically centred; tint only when count > 0 (0 stays plain, muted number).
3. Card outer edges align with the cards below. <= 760 px: counts stack under the text.
Check with 0/0/0, 1/2/3, 0/0/5 and the longest next-action in the pending set, at 1440 px, 760 px
and print. Run python scripts/check.py --browser; list files changed; then stop. No branches, tags
or commits.