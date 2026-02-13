# Engineering Practices

## MVP to long-term growth

**Q:** Your team delivers a Flutter MVP that users love, but the codebase is messy and hard to extend. You are asked to prepare it for long-term growth. How would you systematically improve the architecture, testing, and tooling without stopping feature delivery?

**Key answers:**

- Add "guardrails first": strict lints, formatting, CI checks (analyze/test), and pre-commit hooks so new code can't worsen quality.
- Refactor incrementally with a "strangler" approach: pick one feature slice, introduce boundaries (UI/state/domain/data), and migrate screen-by-screen behind stable interfaces.
- Add characterization tests around current behavior (unit for pure logic, widget tests for key UI behaviors) before refactors; keep shipping by budgeting fixed capacity per sprint for tech-debt paydown.

---

## Quick hack for demo

**Q:** A stakeholder wants "just a quick hack" for a demo in two days. How do you propose a plan that delivers the demo while still keeping the project on an engineering track (maintainable, testable, scalable)?

**Key answers:**

- Offer a two-track plan: (1) demo slice with feature flags and hardcoded/stubbed data, (2) immediately after demo, convert stubs into real implementations with tests.
- Timebox the hack and document "debt IOUs" (what was compromised, why, and the cleanup tasks with estimates).
- Ensure the hack still respects basic boundaries (no business logic in widgets; keep logic in a controller/BLoC/use-case).

---

## Reactive/declarative principles

**Q:** You join a project where developers think of Flutter as "just UI widgets" and keep adding imperative logic in callbacks. Features start breaking randomly. How would you explain and apply Flutter's reactive/declarative principles to reorganize this code?

**Key answers:**

- Explain: UI should be a pure function of state; callbacks only dispatch events that update state, then the UI rebuilds from that state.
- Move logic out of callbacks into a state layer (Notifier/BLoC/ViewModel), make state immutable (copy-with), and centralize side effects in a repository/service layer.
- Introduce predictable state transitions: events → reducer/handler → new state → render, plus tests on the transition logic.

---

## One-file app → engineering

**Q:** You inherit a Flutter app where everything is in one file and "works," but adding features always breaks something else. How would you show the team the difference between "just programming" and engineering, and what concrete changes would you introduce?

**Key answers:**

- Show failure modes: no boundaries, no tests, no contracts, no observability → changes cause regressions.
- Introduce modules and contracts: feature folders, repositories, use-cases, DTO/domain separation, and a consistent state management approach.
- Add quality loops: test pyramid, CI gating, code review checklist, and measurable goals (crash-free %, build time, test time).

---

## Rushed feature vs refactor

**Q:** Management wants a new feature rushed in three days, but implementing it properly requires refactoring a core module. How do you communicate and justify an engineering-oriented approach while still being realistic about deadlines?

**Key answers:**

- Present options with risk/impact: (A) fast patch with known risks + explicit follow-up, (B) refactor+feature with staged delivery.
- Propose a thin vertical slice that doesn't worsen the core module (wrap old code with an adapter, implement new code behind interface).
- Negotiate scope: deliver must-have behavior now, postpone "nice-to-have" UI polish.

---

## Flutter vs native / React Native

**Q:** Your company is deciding between maintaining separate native apps, using React Native, or standardizing on Flutter for mobile and desktop. You are asked to recommend a path. How do you evaluate Flutter's strengths/weaknesses for their product roadmap, and what do you suggest?

**Key answers:**

- Evaluate by product needs: UI richness, time-to-market, platform coverage (mobile/desktop/web), plugin maturity, and team skills.
- Validate with a spike: build one real "hard" feature (animations, offline, auth, deep links) and measure performance + dev speed.
- Suggest a phased strategy: Flutter for shared UI/features, keep native for niche platform-heavy modules if needed.

---

## WebAssembly and client technology

**Q:** A backend team wants to expose features via WebAssembly in the future. How would you argue for or against Flutter as the main client technology in this evolving ecosystem?

**Key answers:**

- Treat WebAssembly as an implementation detail for compute-heavy logic; clients still need UI, state, storage, and platform integrations.
- If shared core logic is needed across platforms, consider: Dart-only shared logic, or WASM for specific algorithms with clear boundaries.
- Decide based on integration cost: if WASM becomes critical everywhere (including web), ensure the chosen client stack can call it cleanly (via FFI on native, JS interop on web).
