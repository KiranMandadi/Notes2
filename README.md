Check only - change no files. Report Remedy field codes/names and yes/no only, never values or
change text.
For the Quality report data (enterprise profile, api backend):
1. Change Coordinator: is it in the enterprise field map? Is it fetched in the Remedy read? Is it
   passed into the report view model / contract? Which Remedy field (code + name)?
2. Today's "Requested by": which Remedy field does it come from (Submitter, Requested By,
   Customer, or other)? Is the Submitter field mapped and fetched as well?
3. Submit Date: is it mapped, fetched and in the report data? Which Remedy field?
4. Lead time: which date is it computed from (Submit Date, Requested Start Date, or other), and
   to which date (Scheduled/Planned Start)?
5. Requested Start / End Date: mapped and fetched? (for awareness only)
For each item, say what would be needed to show it on the report if it isn't already available
(display only / view model / fetch / field map), and whether it touches profiles/enterprise.
Also confirm none of these people fields are written to history.db.
Answer as a short table; then stop. No branches, tags or commits.