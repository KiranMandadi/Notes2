Check only, then fix if needed: does shared mode work the same on Windows, macOS and Linux?
1. cr_core/ui/addresses.py: how does it list interface addresses on each OS? It must work on all
   three with the standard library only (no ifconfig parsing assumptions); fall back safely
   (hostname + 127.0.0.1) and never crash or list an address the machine doesn't have.
2. Default launch: confirm `crq ui` with the enterprise profile starts shared (0.0.0.0:8765) on all
   three, and `--local` gives today's behaviour.
3. Headless server (Linux VM, no browser): `crq ui` must not fail if no browser is available; add
   `--no-open` if missing and say so in the start output.
4. Credentials: confirm the keychain / Windows Credential Manager / Linux (secret service or
   documented fallback) path for the read-only account works without a desktop session; if not,
   say what's needed (no password in plain files).
5. Tests: simulate each OS (mock platform + interface data) for discovery and Host check; mark any
   test that can only run on one OS.
Report per OS (works / needs change). Fix only what's needed; run python scripts/check.py --browser;
list files changed; stop. No branches, tags or commits.