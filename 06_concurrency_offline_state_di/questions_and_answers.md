# Concurrency, Offline, State & DI

## Concurrency & Task Handling

### Dashboard fetches several APIs — UI freezes

**Q:** A dashboard screen fetches several APIs and processes data heavily before showing charts. The UI freezes during loading. How would you redesign the async and concurrency model to keep the UI responsive?

**Key answers:**

- Fetch concurrently (Future.wait) and stream partial results to UI to avoid "all-or-nothing" blocking.
- Move heavy transforms off the UI isolate; isolates communicate via message passing and don't share mutable state.
- Cache results and precompute where possible (e.g., on background sync).

---

### Background sync runs multiple times — corrupts data

**Q:** You have a background synchronization that sometimes runs multiple times concurrently and corrupts local data. How would you structure your async code to prevent such race conditions?

**Key answers:**

- Enforce single-flight sync (mutex/lock/queue) and idempotent operations.
- Use transactions and unique constraints in local DB to prevent duplicates.
- Track sync state and cancel/merge overlapping runs.

---

## Flutter's Single UI Thread

### Synchronous JSON parsing blocks UI

**Q:** A teammate writes a synchronous JSON parsing function that blocks the UI when processing large responses. How would you explain Flutter's single UI thread rule and refactor this task?

**Key answers:**

- Explain that heavy synchronous work blocks frame rendering and causes jank (misses the ~16 ms budget).
- Move parsing to an isolate (compute/custom isolate) and return parsed models asynchronously.
- Add performance tests or profiling to prevent regressions.

---

### Animation drops frames when heavy calculation runs

**Q:** An animation drops frames when a heavy calculation runs. What would you do to separate UI rendering from computation?

**Key answers:**

- Offload computation to an isolate (no shared memory; message passing).
- Reduce per-frame work: precompute, memoize, and avoid rebuilding large subtrees during animation.
- Use RepaintBoundary to isolate repaints.

---

## Async Tools & Isolates

### Poll API, transform, update UI in real time

**Q:** You need to poll an API, transform results, and update the UI in real time. How would you combine Futures, Streams, and cancellations to implement this robustly?

**Key answers:**

- Use a Stream pipeline: timer/trigger → async fetch → transform → emit state.
- Support cancellation (dispose cancels subscription) and debounce/backoff on failures.
- Keep state updates atomic so UI always reflects a consistent snapshot.

---

### ML model 300 ms per inference on device

**Q:** A machine-learning model must run entirely on device and takes 300 ms per inference. How would you use isolates to integrate this without making the UI stutter?

**Key answers:**

- Run inference off the UI isolate and return results via messages; isolates don't share state.
- Batch requests and drop stale requests (only latest inference matters for some UIs).
- Warm up model and cache resources to reduce spikes.

---

## Offline Strategy

### Note-taking app — offline, sync later

**Q:** You are building a note-taking app where data must be available offline and synced later. Describe your strategy for local storage, conflict resolution, and UI feedback when sync fails.

**Key answers:**

- Use local-first writes (local DB), plus an outbox queue of pending mutations.
- Conflict resolution: per-record versioning (updatedAt), or CRDT-like merging for text if needed; surface conflicts to user when ambiguous.
- UI: clear sync status, retry, and "last synced" indicators; never block reading offline.

---

### Online-only app — retrofit offline-first

**Q:** Your existing online-only app starts getting complaints from users with unstable connections. How would you retrofit offline-first behavior without rewriting the entire app?

**Key answers:**

- Add caching at repository level (read from cache, refresh in background).
- Add request retry/backoff and partial offline modes per feature.
- Incrementally persist critical screens first (home, details, drafts).

---

### Data duplicated or lost after reconnect

**Q:** During testing, QA reports that data sometimes gets duplicated or lost after reconnecting from offline. What checks and patterns would you introduce to ensure data integrity during background sync?

**Key answers:**

- Make sync idempotent (use stable IDs, server upserts) and store sync tokens/checkpoints.
- Add dedup constraints locally (unique indexes) and reconcile by IDs.
- Add sync logs + integration tests that simulate offline/online flapping.

---

## State Scope & Tools

### Cart visible on multiple screens; filters local to one

**Q:** In a shopping app, the cart must be visible and up to date on multiple screens, while some filters are local to one screen. How would you scope local vs global state and which tools would you pick?

**Key answers:**

- Cart: global state (app-level store/repository) with persistence; filters: local state in the screen/store scoped to that feature.
- Choose a tool consistent with team: Provider/Riverpod for simpler reactive state, BLoC for event/state rigor.
- Keep derived state (totals, availability) computed from cart state, not duplicated.

---

### Provider, BLoC, and GetX mixed — hard to debug

**Q:** You join a project that uses Provider in some places, BLoC in others, and GetX in a few more. Features work but are hard to debug. How would you rationalize and possibly consolidate the state management approach?

**Key answers:**

- Inventory current usage and choose one primary approach; keep others only where justified.
- Migrate incrementally: new features use the standard; old features are migrated when touched.
- Standardize debugging and patterns (where async lives, error handling, logging).

---

## DI in Flutter

### Services created with new Service() in widgets — need mocks

**Q:** The app currently creates services directly inside widgets with new Service(). You now need to mock those services in tests. How would you introduce DI so that existing code can be migrated gradually?

**Key answers:**

- Start by injecting services via constructors at feature boundaries (screens/controllers), with sensible defaults temporarily.
- Introduce a DI container or provider at the app root and route dependencies from there.
- Gradually remove new Service() from widgets; add tests that use mocks/fakes.

---

### get_it (with or without injectable) — avoid "global God container"

**Q:** You decide to use get_it (with or without injectable) in a large project. How would you organize registration, lifecycles (singleton vs factory), and environment-specific dependencies to avoid a "global God container"?

**Key answers:**

- Register per feature/module (each module exposes a register()), and keep the root only orchestrating module registration.
- Use singleton for stateless/shared services, factory for short-lived objects (BLoCs/ViewModels), and scoped lifetimes for flows.
- Bind environment-specific implementations (dev/stage/prod) via configuration and keep selection logic out of UI.

---

### Code reviews devolve into style debates

**Q:** Code reviews in your team often devolve into style debates. How would you design and implement a linting rule set (analysis_options) to enforce style and catch common issues automatically?

**Key answers:**

- Adopt a standard baseline (Flutter/Dart recommended lints) and add only rules that prevent real bugs.
- Encode architecture rules where possible (forbidden imports, layer boundaries) using lint tooling.
- Make CI fail on lint/format issues; code review focuses on design, not whitespace.
