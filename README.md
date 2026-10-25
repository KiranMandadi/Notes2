Build Phase 1 of docs/plans/comparison-key.md together with two agreed UI changes.
No branches, tags or commits; codes and counts only.

A. Comparison of past changes - accept CK1-CK9 as proposed:
- CK1 chain: closest similar past changes of the product (min similarity 0.35, up to 30, at least 10);
  else all past changes of the product; else "Not enough comparable past changes" with no history notes.
- CK2/CK3 signals, weights, thresholds as in the plan; deterministic; reuse the history cache; no new
  Remedy requests.
- CK4 cohesion gate 0.3: hide task notes when the comparison set's tasks are not alike enough.
- CK5 switch to closest set: history comparison rows (window, tasks, backout, deployment) and Create
  suggestions (CK8). Keep the product for: CI notes, approval timing, platform pattern, overlap check,
  product rule files, track record.
- CK6 wording: "Compared with N similar past changes of <PRODUCT> (same team and CIs)"; when falling
  back: "Compared with N past changes of the whole product (no closely similar changes found)"; with
  Technical details on, list the signals used and the CRQ ids compared. Same on the Executive brief.
- CK7 rename "Service" to "Product" in everything people read (header, At a glance, reports, brief,
  Pending, Rules page, docs, agent instructions); code names may stay.
- CK9 proof: scores, statuses and findings identical on all 6,461 + 16 reviews; only history sections may
  change - report before/after counts per note type, and which changes fall back to product.

B. UI: hide the "Track record" card on the Quality report and its one line on the Executive brief.
   Keep the calculation (approval timing depends on it); switch it off with a setting, do not delete it.

Update tests, docs (history.md, user-guide.md, contracts.md), the catalogue and CHANGELOG; bump the version;
run python scripts/check.py --browser; restart is up to me. Then stop with the proof and file list.