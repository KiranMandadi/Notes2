Landing page polish - UI and wording only. No logic, backend, rule or scoring changes.
1. Top bar: show Rules always, after Pending (Review · Pending · Rules). Inside the Rules page,
   the rule-set id and sources stay behind Technical details.
2. Footer on every page: remove "Runs only on this computer". Always show
   "ChangeLens · history as of <date>" (date as "24 Oct 2026", Eastern time, same as reports).
   With Technical details on, add "· rule set <id> · v<version>". Same footer on all pages.
3. Button: "Generate" -> "Review change". Disabled until the number is valid, but still clearly a
   button (contrast >= 3:1 for its outline/text). Enter submits.
4. Input: autofocus the number box on load. Placeholder "000001234567". Keep "You can paste the
   whole number."; show "CRQ followed by 12 digits" as a red inline error only after an invalid
   entry (aria-describedby, aria-invalid).
5. Feature cards, wording:
   - Straight from Remedy: "...Nothing in Remedy is changed, and every value can be traced to the
     Remedy field it came from."
   - Ready in seconds: "A full quality report with clear next steps for each issue, or a one-page
     executive brief for approvers. Both are ready to print or share."
   Align each card icon with the first line of its title.
6. Below the cards, one quiet row of two text links, always shown: "Review your team's pending
   changes ->" (Pending) and "See the rules behind every score ->" (Rules).
Keep the headline, subtitle, Open with switch and colours unchanged. Check at 1440 px and 760 px,
Technical details on and off, and print; keyboard order: number box, Open with, Review change,
links. Run python scripts/check.py --browser; list files changed; then stop. No branches, tags or
commits.