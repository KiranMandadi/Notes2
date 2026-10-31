Overlaps by impacted application - measure first, change nothing until I OK. Codes and counts only.
1. Today: overlaps = same product, overlapping window or within 1 h. For the current pending list,
   count overlap pairs, and how many share at least one CI under the "Impacts" relationship vs share
   none vs one side has no Impacts CI.
2. Proposed:
   - main list = overlapping changes that share at least one Impacts CI; label "Overlaps (same
     application)"; each entry names the shared application, e.g. "shares <CI name>";
   - same-product changes with no shared Impacts CI: one collapsed line "Also running in this
     product: N other changes";
   - if either change has no Impacts CI: fall back to the product match, marked "same product (no
     impacted application to compare)".
   Only the "Impacts" relationship counts; other relationship types are ignored.
3. Report per pending change: overlaps today vs proposed (main / also-in-product / fallback), with 5
   example ids each way (work/ only); past changes in counts.
4. List where overlaps show (At a glance, brief "What an approver should know", Pending calendar)
   and what each would display.
Then stop for my OK. No branches, tags or commits.