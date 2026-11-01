Freeze calendar times (CC-05) - measure first, change nothing until I OK.
Rule: each restricted period is ONE continuous interval from 09:00 America/New_York on its first date
to 21:00 on its last date. Everything between is restricted, including all nights; days do not reset
at 21:00. A single-day period is 09:00-21:00 that day. A window clashes only if it overlaps that
interval; touching a boundary is not a clash (ending exactly at 09:00 on the first date, or starting
exactly at 21:00 on the last date). Per-period start/end times may override the 09:00/21:00 default.
1. calendar.yaml: keep the five configured periods' dates exactly as they are; add each period's start
   and end time (default 09:00 / 21:00); schema, validate and docs.
2. Measure in memory on all past + pending: CC-05 findings removed/added, score and status changes,
   pending ids whose status changes (with window vs period edges, times only).
3. Wording: message, ribbon, owner question and evidence show times, e.g. "The window falls in the
   restricted period Wed 4 Nov 09:00 - Sun 8 Nov 21:00"; evidence shows the part of the window inside
   the period, e.g. "Restricted: Wed 4 Nov 09:00 - Thu 5 Nov 06:00". Rules page and Pending calendar
   bands show the times too.
4. Exception and "calendar not set" behaviour unchanged.
5. Tests: overnight before the first date (no clash), running into 09:00 on the first date, fully
   inside, a night in the middle of a multi-day period (clash), ending after 21:00 on the last date,
   starting exactly at 21:00 on the last date (no clash), ending exactly at 09:00 (no clash),
   single-day period, the 1 Nov EDT/EST switch.
6. Only the freeze periods get times. Do not change the mainframe online-day / batch critical-path
   hours (MF-05), weekday business hours (CC-08), the "calendar not set" range, or exception handling.
   Proof: MF-05 and CC-08 findings identical on all past + pending; only CC-05 may change.
Then stop for my OK. No branches, tags or commits.