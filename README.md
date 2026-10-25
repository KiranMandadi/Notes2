Approved with these changes, then build Phase 1:
1. how_to_meet must never suggest lowering a rating to pass. Rewrite:
   CC-05 "Plan the window outside the freeze period, or record the freeze exception that allows it."
   CC-07 "Plan the window on a weekday, or say in a sentence about the window why it must run at the weekend."
   CV-02 "Use the top levels only when the change really is that urgent or high-impact, and say why in the Notes."
   CV-03 title "A risk level of 4 or 5 is confirmed"; how_to_meet "Check the answers to the risk questions; if the risk really is 4 or 5, confirm it in the Notes."
   Raising a rating (X-04, INF-03, PCF-03, Q-RISK-01) is fine. INF-03: "If the change causes a reboot or outage, rate the impact Medium or higher."
2. Q-COMPLETE-02 how_to_meet: "Fill in the Backout plan field with the steps that return the service to its previous state." (no Notes - that is what Q-COMPLETE-06 flags).
3. Every how_to_meet must stand alone (it also appears in Send to owner without the title). Fix INF-06, PCF-05, X-05, MS-03 and any other "say so / give both / say it".
4. Q-COMPLETE-01: use a placeholder for the configured required fields, like the other numbers.
5. Decisions: (1) show GEN as Minor with "Planned to become Major after the platform review"; Effect on score in the panel uses the effective severity (-5). (2) MS-04 stays advisory; show "Not applied yet: Change Type isn't read" and add the open item. (3) yes. (4) yes, Q-RISK-04 wording as proposed.
6. Owning-team count excludes "To be confirmed".
Show me only the changed rows, then continue. Same ground rules and checks as before; no branches, tags or commits.