Rules: move to the packs (one source of truth), display/wording only:
1. Add the short Applies-to wording as each rule's applies_label in the pack files (GEN-01..06 and
   any other row whose short label lives in page code); remove the page-code table. Side panel,
   crq JSON and docs/rules-catalogue.md use the same label.
2. CV-02 title: "Top levels of Urgency, Impact and Priority are justified" (why line unchanged).
3. CL-03: move "Not applied yet: only mainframe is identified with confidence..." to a
   Classification pack note; the row keeps only the "Not applied yet" chip.
4. Status filter options: "In use" (default; active + advisory, retired folded per pack - today's
   "Current"), "All" (every rule, retired shown inline, "Showing 72 of 72"), "Active", "Advisory",
   "Retired". Rename "Current" to "In use" everywhere it appears (filter, docs/user-guide.md).
Rule-set id may change; findings, scores and statuses must be identical on all past + pending
(proof from an actual re-run). Re-record the enterprise baseline, regenerate the catalogue, run
python scripts/check.py --browser, list files changed, stop. No branches, tags or commits.


git add -A
git status --short
git commit -m "Rules page: Pending-style header and filters, quieter status column, labels in packs"
git push origin main