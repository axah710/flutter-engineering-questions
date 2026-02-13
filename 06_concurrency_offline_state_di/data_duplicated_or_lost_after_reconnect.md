# Data duplicated or lost after reconnect

**Q:** During testing, QA reports that data sometimes gets duplicated or lost after reconnecting from offline. What checks and patterns would you introduce to ensure data integrity during background sync?

**Key answers:**

- Make sync idempotent (use stable IDs, server upserts) and store sync tokens/checkpoints.
- Add dedup constraints locally (unique indexes) and reconcile by IDs.
- Add sync logs + integration tests that simulate offline/online flapping.
