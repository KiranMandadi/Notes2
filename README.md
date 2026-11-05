Executive redesign of the Pending page (Console, `crq ui`). First read .github/copilot-instructions.md, docs/decisions.md and docs/open-items.md. The approved mock-up is described below; build exactly this.

STANDING RULES
- No git operations: no branches, tags, commits or pushes.
- Never read, search or print cr_core/config.py or cr_core/history/config.py (exclude **/cr_core/config.py and **/cr_core/history/config.py from every search).
- Never run `crq login`; never create a real change; REMEDY_ALLOW_CREATE stays off.
- Live Remedy data only: no caching of pending lists or scores in shared mode (pending_cache_minutes stays 0). Refresh always refetches.
- Don't print, log or store passwords, tokens or change text. In your replies, codes and counts only.
- Keep the Host and Origin checks as they are.

1. DEFAULT APPROVER
- New key CHANGELENS_DEFAULT_APPROVER, read from .env only (not YAML, not a CLI flag). Add it to .env.example with a comment: "Login ID whose approvals Pending opens on. Leave empty on a shared Console."
- Validate it as a login ID (letters, digits, . _ -, max 64). If invalid, ignore it, write one warning to logs/crq-ui.log without echoing the value, and behave as if it were empty.
- Empty or unset: Pending opens on all approvers, the headline reads "N changes for your groups", and there is no approver toggle.
- Set: Pending opens filtered to that approver. Headline "Awaiting <id> · N changes". Under it, a link-style toggle "Show all approvers" / "Show only <id>".
- FALLBACK: if the approver is set but the live list for them is empty, show all approvers instead, with an amber status line under the headline (role="status"): "Nothing is awaiting <id> right now, so all approvers are shown." The headline switches to "N changes for your groups" and the toggle reads "Show only <id>". Never show the full list without this line.

2. HEADER (dark navy band, same palette as the Console header)
- Eyebrow "PENDING APPROVAL", the headline above, then "as of <d Mon yyyy, HH:MM> · Times in ET".
- Refresh and PDF buttons at the right of the header. Remove the old summary tiles/pills and the old Refresh/PDF positions.
- No other counts or links in the header.

3. VIEW CARD (white card under the header)
- "View by" select: Risk (default), Impact, Readiness. Keep the choice in the URL (?view=risk|impact|readiness) so a shared link opens the same view; no browser storage.
- Under it, a row of pill tabs (role="tablist", arrow-key navigation): "All" first, then one tab per value.
  - Risk: Critical, High, Medium, Low, Minimal (Remedy 5→1).
  - Impact: Extensive, Significant, Moderate, Minor (Remedy 1→4).
  - Readiness: Ready, Needs work, Blocked, plus "Checking" while a change's score has not arrived yet (scores load progressively; move rows between Readiness tabs as scores arrive, without re-sorting).
- Each tab: coloured dot, word label, and the count in a separate round badge. Show the full Remedy value on hover (e.g. "4 (High)", "1-Extensive/Widespread"). Tabs with 0 changes stay visible at reduced opacity and are still focusable.
- Tab counts reflect the approver toggle and search, not the selected tab.
- Changing View by resets the tab to All.
- Right side of the card: the search box (CRQ, summary, product) and a "Filters" button with a badge showing the number of active filters. The Filters panel is collapsed by default and holds Organisation, Coordinator group and Approver with a Find button (move the existing filter controls here; keep their behaviour).

4. TABLE
- Columns: # | Change (CRQ with copy icon, summary, PRODUCT line) | Window | Risk | Quality (status pill + score) | Report ("Open →").
- Sort: risk descending, then scheduled start ascending. Label above the table: "Sorted by risk, then start time". Don't re-sort when scores arrive.
- "Showing X of N" next to the label.
- Under the window, the duration followed by up to two small tags:
  - "Today" / "Tomorrow" (blue #E0ECFF on #1E40AF): the scheduled start falls on today's / tomorrow's calendar date in America/New_York (and "Today" also when the window has started but not ended). Compute with zoneinfo, not fixed offsets.
  - "Restricted period" (amber #FEF3C7 on #92400E): only when the existing freeze-calendar check would raise CC-05 for this change, so touching a boundary and an approved exception mean no tag. Reuse the CC-05 function; don't write a second overlap check.
- No left accent bar on rows. Red is reserved for Blocked.
- Empty state when search/filters/tab leave nothing: a short sentence and a "Clear search and filters" button.

5. PHONE (< 720 px)
- Header buttons wrap under the headline; tabs scroll horizontally; table rows become stacked cards (CRQ + tags, summary, window, risk, quality, Open). No horizontal page scroll.

6. PDF
- Reflects the current approver mode, View by and tab. Includes the headline, the as-of line and, when it applies, the fallback line. Tags print in colour, plus their text.

7. TESTS (add or extend; all must pass)
- .env parsing: unset, empty, valid, invalid value (warning logged, value not echoed).
- Fallback: approver with changes → filtered and no banner; approver with none → all shown with the banner text; key empty → no toggle.
- Tab counts per view, including zero-count tabs and the Checking → scored move.
- Sort order is stable while scores arrive.
- Today/Tomorrow at ET midnight boundaries, including across the 1 Nov 2026 DST change, and a window already in progress.
- Restricted period tag matches CC-05 exactly: overlap → tag; touching boundary → none; approved exception → none.
- Run the full test suite and `python check.py --audit`; report the counts only.

8. DOCS AND VERSION
- docs/decisions.md: a new entry for the executive Pending page (default approver from .env only, the fallback rule, View by tabs, why the attention line was dropped, tag rules).
- docs/open-items.md: note "Per-user default approver needs sign-in in shared mode; out of scope."
- README Console section and .env.example updated. Bump the minor version and add a CHANGELOG entry.

When done, list the files changed and the test/audit counts. No branches, tags or commits.