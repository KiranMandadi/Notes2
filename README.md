Stage 1 approved with these fixes; apply them, then continue with Stage 2.

1. URL: do NOT put the approver login or the search text in the URL. SECURITY.md is right; keep its rule unchanged. Keep class, date, org, groups, view, tab, sort and layout in the URL. A shared link opens with the recipient's own default approver. Confirm that request logging (logs/crq-ui.log) never records query strings that could hold a login or search text, and add a test for both.
2. Group list: groups with matching changes first (count descending, then name), then a thin divider and the zero-count groups (dimmed, still selectable). Selected groups stay in their position; don't jump on click. The search box filters both sections.
3. Organisation popover: width up to 420 px so names fit; ellipsis plus tooltip only beyond that.
4. Filter buttons: replace the "·" indicator with a 10 px chevron-down icon (SVG, currentColor, muted grey), rotated when the popover is open.

Then Stage 2 as specified. Same standing rules. No branches, tags or commits.

git status
git add -A
git commit -m "Pending: compact filter bar (class, date, organisation, groups, approver), linked counts, URL state"
git push