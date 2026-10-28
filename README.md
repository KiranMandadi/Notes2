Local rules and suppressions at two levels: coordinator group and product. Plan first in
docs/plans/local-rules-scopes.md, then STOP for my OK. No rule or score changes today.

1. Today: describe how product (services/) files work - matching, suppressions, parameters,
   S-<SERVICE>-NN local rules, approval and expiry checks, where they show on reports and the
   Rules page.

2. Proposal - scopes and precedence:
   - New folder rules/groups/<file>.yaml keyed by the exact coordinator group name from
     support_groups.yaml; product files stay keyed by the exact Remedy Product Name.
   - Limits: product > group > global. Suppressions: a rule is off if the product OR the group
     suppresses it (reports name which). Local rules: both apply.
   - Locked rules can never be suppressed or relaxed at any level.
   - Same governance at both levels: reason, approver (team + reference), expiry <= 6 months;
     CODEOWNERS per file.
   - Rule-set id covers group files too.

2b. Local rules at both levels:
   - Group rules G-<GROUP>-NN and product rules S-<PRODUCT>-NN, same YAML schema and existing
     condition/search types as global rules (no code per rule); a change gets its group's and its
     product's rules.
   - They only add checks: they cannot modify, replace or weaken a global rule (loosening is a
     suppression only).
   - New local rules must start as Advisory (status shadow); crq rules measure reports how often
     they fire on past changes; promotion to Active is a reviewed edit.
   - Severity cap: Minor or Major only; Blocker is reserved for global packs.

2c. Validation and display:
   - crq rules validate errors on: a group/product name that matches nothing, duplicate rule ids,
     expired suppressions, a locked rule suppressed, a limit outside its bounds, a local rule above
     Major, a new local rule not starting as Advisory.
   - Rules page: "Product rules and suppressions" becomes "Local rules and suppressions" with a
     Scope column (Group: <name> / Product: <name>), plus reason, approver and expiry; local rules
     listed under their scope.
   - Reports and the brief: "Switched off for <scope> until <date>: <reason> (approved by <ref>)".
     crq JSON: scope on each suppression and local rule.

3. Tests and docs to add (rules-authoring.md, user guide, contracts, CODEOWNERS guidance); confirm
   0 findings, scores or statuses change today (no files exist yet).
No branches, tags or commits.