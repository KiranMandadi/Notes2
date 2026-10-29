Replace "Print" actions with "PDF", display only (no logic, rule, score or dependency changes):
1. Every print button (Quality report, Executive brief "Print one page", Pending "Print summary",
   Rules page, any other): icon = document/download icon, label "PDF", aria-label "Save <page> as
   PDF", tooltip "Opens the save dialog - choose Save as PDF".
2. Before opening the dialog, set document.title so the suggested file name is:
   "<CRQ> - Quality report", "<CRQ> - Executive brief", "Pending changes - <d Mon yyyy>",
   "ChangeLens rules - <d Mon yyyy>"; restore the title afterwards.
3. Keep the existing print CSS unchanged (it is the PDF layout); brief still fits one page.
4. Update every reference: user guide, README if mentioned, contracts/docs, tests and test names,
   aria labels, CHANGELOG. Remove the word "Print" from UI text except inside the save dialog help.
List first every place that says Print or calls window.print(), then change them. Browser tests:
button label/aria, title set during the dialog and restored. Run python scripts/check.py --browser;
list files changed; stop. No branches, tags or commits.