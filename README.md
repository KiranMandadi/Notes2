1. Brief headline on changes after approval (after_approval = true): don't say "before approval" -
   use "Issues found after approval: <next action>". Display only.
2. MF-06 accuracy - measure first, then stop for my OK:
   - Scored MF-06 only when the change names a Db2 object or action (bind/rebind, DBRM, DDL,
     tablespace, runstats/reorg of a tablespace, SQL, plan/package/collection, DCLGEN).
   - A bare "db2" mention with none of those: "Please confirm" note (0 points): "The change mentions
     Db2. If it binds or changes Db2 objects, name the plan, package or collection and the rebind or
     backout steps."
   - "reorg" alone (no Db2 word) is not a Db2 signal.
   Report: MF-06 scored findings removed/kept, notes added, score and status changes past/pending,
   pending ids affected (expect CRQ000002465323), 5 example ids each way in work/ only.
No branches, tags or commits.