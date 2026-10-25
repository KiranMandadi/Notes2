Decisions on docs/plans/timezone.md: TZ1 together (display and rules on US Eastern). TZ2 yes
(display_timezone: America/New_York in config/reports.yaml; labelled UTC if unset). TZ3 yes (timezone:
America/New_York in config/calendar.yaml, part of the rule-set id). TZ4 yes (every duration and comparison
on UTC instants; convert only to read a date, weekday or hour). TZ5 yes ("Times in ET" once per page;
EDT/EST on single quoted times) plus the viewer's local time on hover (browser zone, e.g. "= 12:00 IST").
TZ6 yes (crq doctor and crq rules validate warn when display, calendar and history zones differ).
TZ7: assume Eastern; open item for the Change Management office; note that calendar.yaml freeze dates are
sample dates to be replaced with the real freeze calendar.
Apply everywhere listed in section 2 of the plan (report, brief, Pending, summary, Send to owner, prints,
footer, file names, --from/--to, Create screen); the laptop's zone is used nowhere once display_timezone
is set.
Build Phase 1 with the proof in section 7: per-rule before/after and status split on all 6,461 past +
16 pending (CC-01, MF-05, CC-07 changes as measured; CC-05, CV-04 unchanged); every changed finding
explained by the new clock; durations, CV-10 and history notes identical (including the 46 windows across
a daylight-saving switch); tests for the 2026-11-01 switch and a Friday-evening start; crq rules validate
examples; new enterprise baseline; CHANGELOG and version bump; python scripts/check.py --browser.
No branches, tags or commits; then stop.