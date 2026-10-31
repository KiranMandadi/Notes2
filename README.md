Approved - build overlaps by impacted component, any product:
- Search: CHG:Associations "Impacts" links made in the last overlap_link_months (default 6, in
  reports.yaml), then those changes' windows; keep overlapping or within 1 h, still to run. Match by
  CI name (no field-map change). Live every time; nothing cached.
- Display: "Overlaps (same component)", each entry "CRQ... · <product> · <window> · shares <CI>
  (<class>)", first 5 then "+N more"; same in the brief. No same-product fallback, no "Also running"
  line. No Impacts CI: "No impacted components listed - overlaps can't be checked".
- Pending summary calendar: same rule; cross-product clashes listed on the change's card
  ("Clash: CRQ... (other product, shares X)"), no new ring drawing.
- Add an accuracy-audit check that compares the 6-month search with an unrestricted one on the
  pending list and reports any missed pair.
Proof: scores, findings and statuses identical; overlap pairs found = 373 on today's list; report
timing median / 90th / max. Update docs, contracts, CHANGELOG, version. Run python scripts/check.py
--browser --audit; list files changed; stop. No branches, tags or commits.