Continue an interrupted task: Stage B of the executive Pending page round 3 (the Quality report as an overlay). Stage A is committed (4a0e5be). Stage B was partly built before the previous chat failed; overlay.js and Pending page hooks exist but are uncommitted and may be incomplete.

First read .github/copilot-instructions.md, docs/decisions.md and docs/open-items.md. Then run read-only `git status` and `git diff --stat` (read-only git is fine; no other git operations) and review the uncommitted Stage B work. Finish it rather than starting over, and fix anything incomplete. Save your progress to files as you go.

STANDING RULES
- No git operations except read-only status/diff/log. If I paste git commands here, don't run them; reply "Git commands go in your terminal, not this chat. Nothing was run."
- Check that .github/copilot-instructions.md contains that rule; add it under the git rules if it's missing.
- Never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env.
- Never run crq login; GET requests only to Remedy; REMEDY_ALLOW_CREATE stays off.
- Live data only; no caching or prefetching of reports.
- No rule, score, finding or status changes; the Quality report's content and behaviour must stay identical.
- Keep the Host and Origin checks and the SECURITY.md URL rule (the approver and search never go in the URL).
- Codes and counts only in replies.

STAGE B SPECIFICATION
B1 Opening:
- "Open →", a row click and a calendar bar click open the change's complete Quality report in an overlay on Pending.
- Ctrl/⌘-click or middle-click on "Open →" still opens the normal page in a new tab.
- The overlay loads the existing report page itself (same route, same server code) in an "embedded" display mode that hides only the report's own top navigation. Never build a second or shorter report.
- Layout: fixed, inset 16 px, with a 72 px dimmed strip on the left (rgba(11,27,51,0.45)), 16 px radius and a large shadow. Full screen on phone.

B2 Overlay toolbar (dark navy):
- "← Back to Pending" with an Esc hint.
- ‹ "7 of 30" › to step through the list's current order, filters, tab and sort (calendar uses the same order). Keys ← / → when the overlay has focus. A "Next: <last 5 digits>" hint, or "Last in list".
- A Technical details switch that drives the report's existing switch, kept when stepping.
- PDF (runs the report's existing PDF) and ×.

B3 Technical details:
- The rule codes and rule side panel work exactly as standalone (reuse the existing component unchanged).
- Esc closes the rule panel first, then the overlay. A click on the dimmed strip closes the overlay only when the rule panel is closed.

B4 Closing:
- Esc, ×, "← Back", a click on the dimmed strip, or browser Back.
- Pending keeps its filters, tab, sort, layout, calendar week and scroll position exactly.
- Focus returns to that row's "Open →". The row is highlighted (#EEF4FB, 3 px navy bar on its left edge) until another change is opened.

B5 "✓ Viewed":
- A grey tag next to the CRQ for every change opened this session, including by stepping. Calendar bars get a small ✓ and "Viewed" in the tooltip.
- Kept in sessionStorage for that tab only; never sent to the server, logged or stored elsewhere. Document this in SECURITY.md.

B6 URL:
- ?open=<CRQ> is pushed as a history entry while open. Back closes the overlay; refresh reopens it; a shared link opens Pending with the report on top.
- An invalid ?open is ignored. The other parameters are unchanged.

B7 Accessibility:
- role="dialog", aria-modal, focus kept inside, a labelled toolbar, and visible key hints.
- The embedded report must not trap Esc.

B8 Performance:
- One report load per open or step, as today. Progressive loading unchanged. Same-origin only. No new endpoints.

TESTS
- Overlay versus standalone: same score, findings, overlaps and freeze section; the rule panel works in both; Esc order.
- Stepping order with filters and sort, and at both ends.
- Pending state preserved after closing; focus return and row highlight.
- ✓ Viewed after opening and stepping, gone in a new tab, and never in requests or logs.
- ?open with Back, refresh, a shared link and an invalid value.
- Ctrl/⌘-click opens a new tab; progressive loading in the overlay; full-screen overlay on phone.
- Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only. Screenshots to work/preview/ at 1440, 1024 and 390 px.

DOCS
- decisions.md entry (overlay showing the complete report, stepping, session-only Viewed, state preserved, Quick look considered and dropped).
- SECURITY.md, CHANGELOG, minor version bump, README and user guide.
- When done, suggest a commit message for me starting with "Pending: Quality report overlay (completes the work described in 4a0e5be)".

No branches, tags or commits.