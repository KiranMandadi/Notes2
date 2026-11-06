Update the Console rule in .github/copilot-instructions.md. Replace the rule that only a person runs crq ui with this, verbatim:

## Running the Console
- Never start, stop or restart the Console on your own initiative.
- When the user explicitly asks in that message (e.g. "restart ui"), you may run `crq ui --restart` (or `crq ui --stop` / `crq ui`) on this local machine only, from the project folder with .venv active. Then confirm the version from /api/status and report it.
- Run it so it keeps running after the chat ends (detached from your shell, if `crq ui` doesn't already detach); say which.
- Never run any crq ui command against the shared Console or the VM, and never change its mode, port or .env settings.

Make only this edit and show me the diff. Don't run anything now.