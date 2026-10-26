Landing page, UI only:
1. Hint under the number box: "You can paste the whole change number, including CRQ."
2. Remove the two text links below the feature cards (Pending and Rules are in the top bar).
3. Review change button states:
   - Disabled (no valid number): outlined style as now; NO hover/active styling, default cursor,
     title "Enter a change number first". Use :not(:disabled) for hover rules.
   - Enabled (valid number): solid teal, white text (contrast >= 4.5:1), slightly darker on hover,
     visible focus ring.
   Switch between them as the user types or pastes.
No other changes. Run python scripts/check.py --browser (include a test that hover on the disabled
button changes no colours); list files changed; then stop. No branches, tags or commits.