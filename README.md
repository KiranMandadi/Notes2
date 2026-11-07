Overlay polish and complete PDF removal. First read .github/copilot-instructions.md, docs/decisions.md and docs/open-items.md. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; never run crq login; GET requests only to Remedy; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Overlay toolbar: remove the Technical details switch.
   - The embedded report must show its own footer with the Technical details switch at the bottom, as on the standalone page.
   - It keeps working as today: the rule side panel opens, and its state carries over when stepping.
   - Esc order is unchanged (rule panel first, then the overlay).

2. Remove PDF and printing support everywhere. Executives have confirmed they don't need it.
   - Remove every PDF button and link: the overlay toolbar, the Pending header, the compact sticky bar, the Quality report, the Executive brief, the Review page, and anywhere else.
   - Remove the server code that produces PDFs: routes, handlers, PDF-only templates and helpers, and any "PDF ready only after overlaps" logic.
   - Remove the print stylesheet and all print-only CSS, markup and JS (@media print rules, print-only headings and filter summaries, "hide when printing" classes). Browser printing will simply show the page as on screen.
   - Remove PDF-only dependencies from pyproject.toml (and the lock file if one exists), only after checking nothing else uses them.
   - Remove PDF-only config keys and their docs. Old config files that still contain them must load without error: ignore the key and write one warning to the log.
   - Search the repo case-insensitively for "pdf", "print", "@media print", "weasyprint" and similar, in code, templates, tests, docs, README, the user guide, .github files and scripts. Remove every remaining reference. Report anything left and why (past CHANGELOG entries stay as history; unrelated uses of the word "print", such as Python print calls, are fine).

3. Overlay backdrop:
   - Replace the dark scrim with a near-white one: rgba(244,246,250,0.88) with backdrop-filter: blur(2px), falling back to the plain colour where blur isn't supported.
   - The Pending page behind, including its navy header, must look washed out, not dark.
   - Give the overlay a 1 px #CFD7E3 border and a stronger shadow (0 24px 64px rgba(11,27,51,0.28)) so it stands out on the light backdrop.
   - Keep the 72 px left strip clickable to close, with a "Back to Pending" tooltip.

4. Tests and checks:
   - The overlay toolbar has no Technical details switch; the report's footer switch works inside the overlay, and the rule panel opens.
   - No PDF route exists (404 for the old routes), no page shows a PDF button, and no PDF dependency remains.
   - No @media print rules or print-only code remain.
   - Old config files with the removed PDF keys still load, with one warning.
   - The overlay backdrop is the light colour.
   - Remove or rewrite every existing PDF and print test.
   - Run the full suite and `python scripts/check.py --browser --audit`; confirm zero score differences; report counts only.
   - Screenshots to work/preview/ at 1440 and 390 px.

5. Docs:
   - decisions.md entry: PDF and printing removed (executives confirmed they don't need it); Technical details lives only in the report footer; light overlay backdrop.
   - Update README, the user guide, SECURITY.md and operations.md wherever they mention PDF or printing.
   - CHANGELOG and a minor version bump.

Stop when done and report counts, plus the list of files changed. No branches, tags or commits.