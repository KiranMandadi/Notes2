Pending page, display only: the Brief button's "Opening..." state overflows and is clipped by the
table card. Fix:
1. Keep the label "Open" in every state; while loading, replace only the arrow with a small spinner
   of the same size, so the button width never changes.
2. Give the Brief column a fixed min-width that fits the button and its padding at 1440, 1280 and
   760 px; nothing in that column may overflow the card (check with overflow visible in tests).
3. While loading: disabled, aria-busy="true", aria-label "Opening <CRQ>"; a second click does
   nothing. On error, restore "Open →" and show the existing error card, not text in the button.
Add a browser test that clicks Open and checks the button stays inside the card. Run
python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.


git add -A
git commit -m "Pending page: day-based durations, stable Open button"
git push origin main