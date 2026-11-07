Review Decision for the change review meeting, and removal of "Send to owner". First read .github/copilot-instructions.md, docs/decisions.md and docs/open-items.md. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; never run crq login; GET requests only to Remedy; live data only; no rule, score, finding or status changes; codes and counts only in replies.

PART A: Remove "Send to owner" completely
- Remove the button from the standalone Quality report, the overlay and anywhere else.
- Remove everything that exists only for it: routes, handlers, templates, JS, CSS, config keys, email or message helpers, and agent or doc references.
- Old config files that still contain its keys must load without error: ignore the key and log one warning.
- Remove or rewrite its tests. Add a test that the old route returns 404 and no page shows the button.
- Search the repo case-insensitively for "send to owner", "send_to_owner", "sendToOwner" and similar. Report what remains and why (past CHANGELOG entries stay as history).

PART B: Review Decision (session-only)

B1. What it is
- Label: "Review Decision". Values: Approve, Needs work; none means "Not decided".
- It's a meeting record only: it never writes to Remedy and never affects scores, findings or status.
- No notes field.

B2. Storage
- Keep decisions in sessionStorage for the current browser tab, keyed by change number, alongside the existing ✓ Viewed data.
- They survive a refresh and are cleared when the tab closes.
- Never send them to the server, never put them in the URL, never log them, and never store them anywhere else.
- Make sure the overlay's embedded report and Pending share the same tab-scoped store.

B3. Control in the overlay and the standalone report (where "Send to owner" was)
- "Review Decision" label with two buttons, Approve and Needs work (role="radiogroup"; each aria-pressed).
- The selected button is filled: Approve #E3F4EA background with #1E6B45 text; Needs work #FDF0DC with #8A4B08. Unselected buttons are white with a #CFD7E3 border. Clicking the selected one again clears it.
- Keyboard shortcuts A (Approve) and N (Needs work), but not while typing in an input.
- "Move to next after deciding": a small tick box next to the control, on by default, remembered in sessionStorage.
  - When on, recording a decision in the overlay shows the filled state for about 400 ms, then steps to the next change in the list's order, using the existing stepping (including the wait-for-previous-report behaviour).
  - At the last change it stays put and shows "Last in list".
  - The standalone report doesn't step.

B4. Pending
- Next to "✓ Viewed", show a decision pill with the same colours as B3: "Approve" or "Needs work". Nothing when not decided. Calendar bars get a small matching dot, and the tooltip includes the decision.
- On the results line (with "Sorted by …", "Showing X of N" and the search), add:
  - "Decided N of M" (M = changes in the current filtered list);
  - a "Copy Decisions" button;
  - a "Clear decisions" link, with a confirm dialog that clears all decisions for this tab.
- Pills and the counter update immediately when the overlay closes, or when a decision is made in another view in the same tab.

B5. Copy Decisions
- Copies only changes that have a decision, from the current filtered list, grouped as all Approve first, then all Needs work, sorted by change number within each group.
- Two columns: "Change number" (the full CRQ) and "Review Decision".
- Write two clipboard formats at once:
  - text/html: a clean table (header row, thin borders, no colours that clash in Outlook or Teams);
  - text/plain: tab-separated, with a header line.
- Use the same clipboard approach and fallback as the existing CRQ copy icon, which works on the VM opened by IP over plain http.
- Afterwards, show a brief confirmation "Copied N decisions". With nothing decided, the button is disabled, with the tooltip "No decisions yet".

B6. Protection against losing work
- If any decision was made or changed since the last Copy Decisions, closing or reloading away from the tab shows the browser's leave-page warning.
- Copying clears that pending state; any later change sets it again.

B7. Accessibility
- Visible focus rings; the pills and the counter are announced; the copy confirmation uses role="status".

TESTS
- Part A: no button, the old route returns 404, old config keys still load with a warning.
- Decisions:
  - recording, changing and clearing; the A/N keys, but not while typing;
  - auto-advance on and off, and at the last change;
  - persistence across a refresh, gone in a new tab;
  - nothing in requests, the URL or logs.
- Pending: the pills, the calendar dots and tooltips, "Decided N of M" with filters applied, Clear decisions with its confirm.
- Copy Decisions:
  - only decided changes, Approve group first, sorted by change number within each group;
  - both clipboard formats and their exact contents;
  - disabled when empty; the fallback path.
- The leave-page warning fires only when there are uncopied decisions.
- Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only.
- Screenshots to work/preview/ at 1440 and 390 px: the overlay with the control, Pending with pills and the counter.

DOCS
- decisions.md:
  - Send to owner removed;
  - Review Decision is session-only, Approve/Needs work, no notes, never written to Remedy;
  - auto-advance; Copy Decisions format; the leave-page warning.
- Update SECURITY.md (decisions stay in the browser tab only), the user guide (the meeting workflow: open, decide with A/N, Copy Decisions, paste into email or Teams), README, CHANGELOG, and a minor version bump.

Stop when done and report counts, plus the list of files changed. No branches, tags or commits.