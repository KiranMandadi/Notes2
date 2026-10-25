Decisions on docs/plans/accuracy-audit.md:
- AA1 yes - apply E now (I approve; pack owners are informed, not a blocker): add the strong terms to
  MF-03, MF-06, MF-04, CFG-02, GEN-02, INF-07 and accept joined/hyphenated forms of multi-word terms.
- AA2 yes (GEN-03 word forms). AA3 yes (remove Deployment strategy from look_in where it can never match).
  AA4 yes (GEN-01 pattern on one line). AA5 yes (evidence wording C: "Looked for / Searched / not found",
  looked_for per word group, no highlighted box for a search; same in Send to owner, brief, agents, JSON).
- AA6: D1 after E - a strong near-miss in long searched text becomes "Please confirm: <item> - we could
  not find it clearly", 0 points. Do NOT apply D3.
- AA7: MF-01 - naming CICS/IMS/Db2 without a region name -> "Please confirm" (D1), until a mainframe owner
  decides; add an open item.
- AA8: open item - measure how often a Backout plan exists only as an attachment; no attachment reading yet.
Build Phase 1 in the order E, F, G, C, then D1. Proof: per fix, before/after per rule and status split on
all 6,461 past + 16 pending; every changed finding explained by its fix; crq rules validate with pass/fail
examples for every new word; CRQ000002456603 shows no MF-03 and MF-01 as "Please confirm"; 5 spot-check
ids per fix. Bump pack versions, new enterprise baseline, update catalogue/CHANGELOG, run
python scripts/check.py --browser. No branches, tags or commits; then stop.