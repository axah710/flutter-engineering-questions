# Background sync runs multiple times — corrupts data

**Q:** You have a background synchronization that sometimes runs multiple times concurrently and corrupts local data. How would you structure your async code to prevent such race conditions?

**Key answers:**

- Enforce single-flight sync (mutex/lock/queue) and idempotent operations.
- Use transactions and unique constraints in local DB to prevent duplicates.
- Track sync state and cancel/merge overlapping runs.
