# Coding Rules, CI/CD, Documentation, Testing & Environments

## Coding Rules & Automation

### New developer bypasses formatting and analysis

**Q:** A new developer pushes code that bypasses formatting and analysis. How would you use tooling (pre-commit hooks, CI) to enforce rules without relying on manual policing?

**Key answers:**

- Add pre-commit hooks for dart format + flutter analyze + unit tests.
- CI is the final gate: fail builds if formatting or analysis differs.
- Provide "one command" scripts (makefile/task runner) so compliance is easy.

---

### Frequent merge conflicts and broken main

**Q:** Your team has frequent merge conflicts and broken main branch builds. How would you set up a Git workflow and CI for a Flutter app to minimize these issues?

**Key answers:**

- Use trunk-based or short-lived branches with PRs, required reviews, and required CI checks before merge.
- Run CI on PR: analyze, unit/widget tests, and at least one integration smoke test.
- Enforce small PRs and frequent rebases to reduce conflicts.

---

### Automated builds for dev/stage/prod with flavors

**Q:** You need automated builds for dev/stage/prod with different flavors and environment configs. How would you design the CI/CD pipeline to handle this smoothly?

**Key answers:**

- Use Flutter flavors as per Flutter deployment docs for Android/iOS.
- Inject environment values with build-time config (e.g., --dart-define), and keep secrets in CI secret storage.
- Produce signed artifacts per flavor, and publish to separate tracks (internal testing / TestFlight groups).

---

## Documentation

### Critical feature only in senior's head

**Q:** A critical feature exists only in one senior developer's head. When they go on vacation, nobody can fix a production bug. What documentation would you introduce and how would you keep it up to date?

**Key answers:**

- Add runbooks (how to debug/operate), ADRs (why decisions were made), and a short architecture overview.
- Document critical flows with sequence diagrams and "failure modes" (what breaks, how to recover).
- Keep docs close to code and require doc updates in PRs that change behavior.

---

### Big docs folder outdated — nobody reads it

**Q:** The project has a big docs folder that no one reads because it is outdated. How would you redesign the documentation process so that it remains "living" and trustworthy?

**Key answers:**

- Replace big docs with small, owned docs: one-page per feature/module, updated by owners.
- Automate parts (API docs, build commands) and keep examples executable.
- Add "docs freshness" checks (last updated, required sections) and delete stale content aggressively.

---

## Testing Strategy

### Production bug after simple refactor despite "some tests"

**Q:** A production bug appears after a simple refactor, even though "some tests" exist. How would you design a testing strategy (unit/widget/integration/golden) for a key feature to avoid this in the future?

**Key answers:**

- Unit-test domain rules and use-cases; widget-test UI states and edge cases; integration-test critical end-to-end paths.
- Add golden tests for visually sensitive screens to catch pixel-level regressions.
- Ensure tests run in CI on every PR; prioritize stable, deterministic tests.

---

### Complex widget sensitive to UI regressions

**Q:** You implement a complex widget that is very sensitive to UI regressions. Describe how you would set up widget and golden tests to ensure future changes do not break its visual appearance.

**Key answers:**

- Build test harnesses for each state and size class (phone/tablet, light/dark).
- Use golden tests for snapshots; keep fonts/assets deterministic in CI.
- Add widget tests for interactions and semantics (tap/scroll/focus).

---

### Payments and authentication integration tests

**Q:** You are integrating payments and authentication flows. How would you use integration tests to cover these critical paths, including error scenarios?

**Key answers:**

- Use Flutter's integration_test package for end-to-end testing on devices/emulators.
- Cover success + failure cases (network errors, canceled payments, expired tokens) with test doubles or sandbox backends.
- Add smoke tests to run nightly and a smaller subset per PR.

---

## Multiple Environments & CI

### Dev, staging, production backends — flavors and config

**Q:** Your app must connect to dev, staging, and production backends with different keys and endpoints. How would you set up flavors and configuration management so switching environments is trivial for both developers and CI?

**Key answers:**

- Create dev/stage/prod flavors using Flutter flavor setup guides.
- Load endpoints/keys from build-time configuration (CI injects secrets; local uses non-secret defaults).
- Keep a single config interface in Dart so code doesn't branch everywhere.

---

### Release process fragile and manual

**Q:** The release process is fragile and manual, causing last-minute mistakes. How would you use CI/CD plus flavors to create a reliable, repeatable release pipeline?

**Key answers:**

- CI builds signed artifacts per flavor, runs tests, and tags releases automatically.
- Separate approval steps (manual promote) from build steps (automated) to reduce human error.
- Use staged rollout and monitoring gates (crash-free sessions, key metrics).
