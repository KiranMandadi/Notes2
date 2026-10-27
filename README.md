Build both now. Organisation and coordinator-group filters: "Organisation" drop-down (default "All
organisations", then the organisations from support_groups.yaml in file order) and "Coordinator
group" drop-down (first item "All coordinator groups", then that organisation's groups; disabled
until an organisation is chosen; resets when the organisation changes). Options show pending counts
("Settlement Systems Support (3)"); groups with 0 listed last and greyed. Client-side, applies
instantly, page state only (no URL). The approver filter, status chips and these filters all
combine; the header count and subtitle (e.g. "8 changes · Settlement Systems Support"), tiles, chips,
table and Print summary follow the filtered list. "Clear filters" link when any filter is active.
Empty result: "No pending changes match these filters." Report how many pending changes match no
organisation in the yaml (expect 0). Labelled selects; keyboard order organisation -> group ->
approver -> chips.