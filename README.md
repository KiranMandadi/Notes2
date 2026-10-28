Rules page polish, display only (no rule, pack or scoring changes):
1. Filter bar like the Pending page: grid row [Search ~60%][Severity][Status][Showing N of 72];
   all controls 40 px high, same border, radius, font and focus ring as the Pending filters; labels
   in the same small uppercase style on one baseline; "Showing" text vertically centred.
2. Header: same dark band as Pending - title "Quality rules", purpose line, the defaults note, and
   the four count tiles (Active 60, Advisory 6, Locked 6, Retired 6) styled like Pending's tiles.
3. Cross-platform pack and CL-03: the "Not applied yet: only mainframe is identified with
   confidence..." text once in the pack note (CL-03: once under its row); each affected row shows a
   small grey "Not applied yet" chip instead of the full sentence.
4. General application: the "Planned to become Major after the platform review" text once in the
   pack note ("...counts as Minor in this first release; planned to become Major after the platform
   review (GEN-03 at High risk only)"); rows show just the severity badge. Shorten each GEN row's
   Applies to: "Non-mainframe changes that mention a deployment" / "...a database script".
5. Within each pack, list rules in code order (Q-COMPLETE-01..07, then Q-SAFETY, Q-VAGUE...).
6. Name the section "Organisation rules" in both the side list and the heading.
7. Side list: normal text colour (contrast >= 4.5:1), counts muted; highlight the section in view
   while scrolling (IntersectionObserver), keyboard-focusable links.
8. Team validation note: hide "(config/support_groups.yaml)" unless Technical details is on.
9. Status column: no "Active" label for an ordinary active rule; show only chips that differ
   (Advisory · 0 pts, Locked, limit, ChangeLens default, Not applied yet). Add a one-line legend
   under the tiles: "Rules with no status chip are active and count towards the score."
Check 1440, 1024, 760 px and print (print keeps the full catalogue, notes included). Run
python scripts/check.py --browser; list files changed; stop. No branches, tags or commits.