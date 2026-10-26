Quality report summary block, UI only:
1. Use the same two-column grid (same column widths and gap) as Issues to fix / At a glance below,
   so the summary's edges line up with those cards.
2. Left card = verdict chip, next-action headline and subtitle line (unchanged content).
3. Right card = one compact counts panel: three equal cells (Blockers · Major · Minor) with thin
   dividers, large number above a small label, vertically centred, same height as the left card.
   Tint a cell only when its count > 0 (Blockers red-tint, Major amber, Minor blue, as today);
   a 0 is plain with the number in muted grey. Text contrast >= 4.5:1 in every state.
4. <= 760 px: right card stacks under the left, as the columns below do. Print keeps one row.
Same on the Executive brief only if it shares this component. Check with 0/0/0, 1/2/3 and 0/0/5,
at 1440 px, 760 px and print. Run python scripts/check.py --browser; list files changed; then stop.
No branches, tags or commits.