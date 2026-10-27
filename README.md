Docs: apply my answers about the two config files (line numbers in brackets). Docs only; no code
changes.

cr_core/config.py
1. CR_PENDING_STATUSES default when unset = "Request For Authorization", "Request For Change" (24);
   an empty list is CONFIG_INVALID (192). Docs: "default 2 when unset; .env.example adds Scheduled
   For Approval". Keep .env.example at 3.
2. CONFIG_INVALID collects every problem and reports them together (195): REMEDY_BACKEND not api;
   REMEDY_BASE_URL missing, not a full URL, or http to a non-local host; REMEDY_USERNAME missing; a
   true/false setting with another value; REMEDY_CA_BUNDLE file not found; REMEDY_TIMEOUT not a
   positive number; CHANGELENS_TODAY not a date; CR_PENDING_STATUSES empty; CRQ_HOME folder not
   found (91); profile problems (139). PROFILE_FILE_MISSING names each missing file (50) with a
   restore hint; crq doctor skips it and reports missing files itself (199).
3. REMEDY_BACKEND defaults to api; any other value, mock included, is CONFIG_INVALID (143-145).
4. The real environment wins over .env (114); REMEDY_ALLOW_CREATE is read only from .env (116, 161);
   CRQ_HOME only from the environment (86-87); an empty value counts as not set (121-123), so
   check.py's placeholder wins over an empty REMEDY_USERNAME= in a copied .env.
5. Defaults: CHANGELENS_PROFILE = DEFAULT_PROFILE (enterprise); REMEDY_VERIFY_SSL true;
   REMEDY_CA_BUNDLE none = OS trust store, must exist if set; REMEDY_TIMEOUT 30 s (positive);
   CRQ_DEBUG false (writes logs/crq-debug.log); REMEDY_ALLOW_CREATE false.
8a. config.py: "Reads and validates settings; every bad setting is named in the error."

cr_core/history/config.py
6. deployment_strategy IS an allowed work_info_types key (32). All keys are optional and map a
   logical name to your Remedy's Work Info type name (240); the shipped history.yaml leaves the map
   empty. Docs: "may include", not "should include".
7. history.yaml is optional; missing or empty = defaults (115-123); unknown keys rejected (126).
   Defaults: path "", timezone "" (stored offsets kept), profile_days 180, min_changes_per_service
   10, stale_days 7, incident_after_change_days 7, refresh_after_days 7, closed_statuses Closed/
   Completed/Cancelled/Rejected, closure_map as DEFAULT_CLOSURE_MAP, scope/fields/work_info_types/
   task_name_normalise empty, thresholds as in the Thresholds dataclass.
   Path order: CHANGELENS_HISTORY_DB (config.py:80), then history.path, then the default - find and
   cite where work/history/<profile>/history.db is set.
2b. A bad history.yaml timezone is CONFIG_INVALID with a tzdata hint on Windows (134-136). Find
   where the calendar.yaml timezone and reports.yaml display_timezone are validated, and document
   both.
8b. history/config.py: "profiles/<name>/config/history.yaml: optional; without it the defaults
   apply. It cannot change a verdict."

Also:
- Keep refresh_after_days (when history counts as due) clearly distinct from crq-load refresh's
  4-week reload window in every doc.
- Describe min_changes_per_service as "per product" (key name unchanged).
- Close H7 and D13 in docs/open-items.md if fully answered.

Then re-run the docs accuracy check (expect 0 wrong/outdated/unclear), check every link, run
python scripts/check.py --browser, list files changed, and stop. No branches, tags or commits.