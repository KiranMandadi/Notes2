remedy_field_map.yaml:226 is a routing identifier, not a secret - allowed under D4. Add it to D4's
note in docs/open-items.md ("request_headers gateway identifier includes the company domain;
allowed in the internal repo"). Teach the sensitive-data scan to allow that one line so it stops
flagging it.
Also: list every directory the code expects (under profiles/ and elsewhere) that has no tracked
files; add a .gitkeep only where a fresh clone would otherwise fail (work/ and reports/ contents
stay ignored).
Run python scripts/check.py; list files changed; stop. No commits, branches or tags.