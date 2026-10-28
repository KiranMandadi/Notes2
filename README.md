Phase 2 accepted. Phase 3 (research outputs + shadow rules; no score changes):
1. CC-06: record in D24 "8 h confirmed by history for non-mainframe (evidence card)"; mainframe limit
   to be confirmed with the mainframe owners (link D16/D21). No rule change.
2. New candidate "10 or more configuration items linked": check it within each risk level and class
   first; if it holds, add as a global rule with status shadow (Advisory, 0 points), Minor, title
   "A change touching 10 or more configuration items says how it is staged or verified", with
   looked_for words for staging/phasing/verification; measure with crq rules measure.
3. No platform identified: list the top products, coordinator groups and frequent words among these
   changes (counts only in the doc) and propose how to widen platform identification. No change yet.
4. MF-03: write a one-page evidence card for the mainframe owners (package ID missing -> rework 5x),
   in docs/research/, counts only.
5. Business-hours start: add as shadow Minor, Standard changes excluded, title "A change starting in
   weekday business hours says why it can't run outside them"; define business hours from
   calendar.yaml; measure it.
6. CV-08: propose narrowing to "Technical Design missing" only - measure in memory (findings removed
   past/pending, score/status changes; it is advisory so expect none) and stop for my OK before
   changing the pack.
7. Per-group evidence cards for the 7 groups above peers on rework (one file each in work/research
   with names; doc uses codes only). No local rules.
8. Exclude history before 1 Nov 2025 from future research runs (deployment strategy not loaded);
   note it in the doc.
Proof for 2 and 5: findings, scores and statuses identical (shadow only); new advisory finding
counts on past and pending. Run python scripts/check.py; list files changed; stop. No branches, tags
or commits.