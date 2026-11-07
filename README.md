Fix the Class filter's checkbox states and note. Same standing rules; no git operations unless I ask.

1. Each class row's tick means "included".
   - "All classes" is ticked only when every class is included.
   - It shows the indeterminate state (–) when only some are included, including the default of all except Standard.
   - It is never unticked. Clicking "All classes" when it is ticked or indeterminate selects all; there is no "none" state.

2. Zero-count rows are disabled: greyed, not clickable, skipped by the keyboard, with the tooltip "No pending changes with the current filters" and their tick shown faded. This applies in the default and "All" states too.
   - Exception: in a custom selection (not the default, not "All"), a ticked row that drops to 0 stays enabled so it can be removed.

3. URL: no class parameter for the default; class=all for every class; an explicit list only for a custom selection. Old links whose explicit list equals every class are read as all.

4. Apply the same tick, indeterminate and disabled model to the Organisation and Group popovers wherever they use "All …".

5. Class popover note, above Done:
   - When Standard isn't included: "Standard changes are not included by default." If N > 0, add on the same line: "(N hidden)".
   - When Standard is included: "Standard changes are included."
   - Remove the "pre-approved" wording everywhere it appears: the UI, the user guide and decisions.md.

6. Tests:
   - default state: indeterminate "All", zero rows faded and disabled, Normal enabled;
   - "All" state: every row ticked, zero rows faded and disabled, URL class=all;
   - custom selection where a ticked row drops to 0: still removable;
   - an old URL with a full list;
   - keyboard skipping;
   - the note text in each state, and no "pre-approved" text anywhere.
   Run the browser tests and the audit; report counts.

No branches, tags or commits.


git status
git add -A
git commit -m "Pending: Standard excluded by default, consistent filter checkbox states, zero-count values disabled, product wraps to two lines"
git push