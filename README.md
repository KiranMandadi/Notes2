Docs accuracy check - change no files yet. For every *.md in the repo (README first):
1. Every command, flag, setting, default value, file path, error code, version and count stated
   in the doc matches the code and config today (cite file:line for each mismatch).
2. Every described behaviour is current (e.g. shared vs --local, port handling, freeze calendar,
   advisory wording, Rules page, side panel, Remedy values, limits marked as ChangeLens defaults).
3. No mention of removed features (sample profile, mock backend, docs/design, Create in shared
   mode) except in docs/archive/ and old CHANGELOG entries.
4. Terminology is consistent across docs and the UI: Product name, Advisory, Ready/Needs work/
   Blocked, restricted period, Change coordinator, ChangeLens default.
5. README: lists the right prerequisites, every step works in order, and every link resolves.
Report a table per file: claim, status (ok / wrong / outdated / unclear), fix. Then stop.
No branches, tags or commits.

You are a new engineer who has never seen this project. Read only README.md, then docs/README.md.
Do not read code. Tell me: (1) in one sentence, what this tool does and who it is for; (2) every
term you didn't understand; (3) every step where you would be stuck or have to guess; (4) what you
would expect to find but didn't; (5) anything that felt too long or repeated. Change no files.