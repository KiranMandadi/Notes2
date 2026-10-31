Approved - build the fix as planned (schema 4, key (change_id, ci_id, relationship_type), stable
paging by type, in-place upgrade from v3, docs, tests, version 0.30.0). In the reload instructions
add: stop the Console before the backup copy and the reload; copy only history.db (no -wal/-shm).
In step 2, compare every product's usual platform and every pending score/finding/status before
and after; if any differ, report the product/change ids and stop - do not continue to step 3.
Run python scripts/check.py --browser --audit; list files changed; stop. No branches, tags or
commits.