History pills colour, display only: give every history comparison pill its own colour family,
distinct from severity/status colours (no red, amber or green):
- differences (About Nx longer/shorter, Different, Missing, Check): light-violet fill, dark violet
  text;
- usual patterns (Usually there, Often there): paler violet fill, dark violet text;
- neutral (Same, Varies): grey outline, no fill.
Applies to: Quality report comparison Note column, Executive brief "How this change differs" column,
the brief's "Versus past changes" tile chip, "Last time this change ran", and print. Match the
section's existing violet accent; contrast >= 4.5:1; same size/shape as the severity badges.
Browser test: no history pill uses a severity colour. Run python scripts/check.py --browser; list
files changed; stop. No branches, tags or commits.