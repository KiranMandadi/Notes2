Decisions: any product (label "N from other products" when any peer is); minimum 10 peers; similarity
0.5; differences shown only when task cohesion is 0.7 or more. Why-line order: Same type first, then
Same CIs, Same team, Same platform. Below the gate: "Differences are not shown: these past changes
vary too much (their task lists are N% alike)." No product fallback.
Build as described in section 6 of peer-quality.md. Proof from an actual re-run of every past and
pending change, matching the measurement by tier and difference kind (report the 0.7 gate figures);
scores, findings and statuses unchanged (history never scores). Update contracts.md, the user guide
and CHANGELOG; version bump. Run python scripts/check.py --browser --audit; list files changed; stop.
No branches, tags or commits.