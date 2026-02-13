# Note-taking app — offline, sync later

**Q:** You are building a note-taking app where data must be available offline and synced later. Describe your strategy for local storage, conflict resolution, and UI feedback when sync fails.

**Key answers:**

- Use local-first writes (local DB), plus an outbox queue of pending mutations.
- Conflict resolution: per-record versioning (updatedAt), or CRDT-like merging for text if needed; surface conflicts to user when ambiguous.
- UI: clear sync status, retry, and "last synced" indicators; never block reading offline.
