   Restore .env.example line 15 to REMEDY_BASE_URL=https://remedy.example.com (do not touch .env).
   Update the CODEOWNERS line-1 comment so it no longer mentions <handle>, and update D3 in
   docs/open-items.md: "CODEOWNERS set to a single owner; team handles to be added later".
   Then re-run the sensitive-data scan (expect 0 company hosts and 0 internal URLs) and
   python scripts/check.py. List files changed; stop. No branches, tags or commits.