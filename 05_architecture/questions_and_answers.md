# Architecture

## Critical Role of Architectural Decisions

### V1 quickly but scale to millions

**Q:** A startup asks you to build a "v1" quickly but expects to scale to millions of users. How would you propose an architecture that allows fast development now but leaves room for serious evolution later?

**Key answers:**

- Start with feature-based structure + clear layers (UI/state, domain, data) but keep it lightweight.
- Establish interfaces early (repositories/services) so implementation can evolve without UI churn.
- Bake in observability (logging, crash reporting) and testing baseline from day one.

---

### Chosen architecture makes adding features slow

**Q:** Mid-project, the team realizes the chosen architecture makes adding new features extremely slow. How would you guide an incremental architectural change without stopping feature work?

**Key answers:**

- Identify pain points and define a target architecture (what changes, what stays).
- Migrate incrementally by routing new work through the new boundaries and wrapping old modules with adapters.
- Track progress with a "migration board" and enforce rules (new code must follow target structure).

---

## Variables Influencing Architectural Choices

### New app: small team, complex domain, deadline, offline, multi-platform

**Q:** You are designing a new Flutter app with: small team, complex domain, strict deadline, offline mode, and multiple platforms. How would these constraints influence your architectural choice and why?

**Key answers:**

- Small team + deadline: keep framework choices minimal; choose one state management approach and one DI approach.
- Complex domain + offline: invest in strong domain/data boundaries, repositories, and a sync layer.
- Multi-platform: avoid platform-specific leakage into UI; isolate platform integrations behind services.

---

### Two teams (Android/iOS backgrounds) on one Flutter app

**Q:** Two teams with different Android/iOS backgrounds will collaborate on one Flutter app. How would team skills shape your architectural suggestions?

**Key answers:**

- Use patterns familiar to both (layered architecture, repositories, DI), and standardize naming and folder conventions.
- Provide onboarding docs + examples for the chosen state management and testing style.
- Enforce conventions via lint rules and templates.

---

## Navigating the Architectural Landscape

### Simple layered → Clean Architecture or feature modules?

**Q:** Your current app is a simple layered architecture (UI → logic → data), but you are starting to hit limitations with growing features. How would you decide whether to move to Clean Architecture, add feature modules, or keep the existing structure?

**Key answers:**

- Decide based on symptoms: duplication, unclear boundaries, test pain, feature coupling, build times.
- If features are independent domains, modularize by feature first; add Clean Architecture strictness only where complexity demands it.
- Run a pilot migration on one feature and measure outcome (velocity, defects).

---

### Manager wants "microservices" on mobile

**Q:** A manager wants to "adopt microservices" and asks you to change the mobile architecture to match. How do you respond and what architecture would you propose for the Flutter client?

**Key answers:**

- Explain that microservices are backend deployment; the mobile client should optimize for UX, offline, and maintainability.
- Propose a client architecture with repositories/use-cases and a cohesive local domain model (don't mirror backend service boundaries blindly).
- Use API gateway/BFF patterns server-side if needed to simplify mobile.

---

## Cultivating an Architectural Mindset

### Bug keeps reappearing in different modules

**Q:** A bug keeps reappearing in different modules, suggesting a systemic design problem. How would you use an architectural mindset to identify root causes instead of just patching each bug?

**Key answers:**

- Look for common causes: duplicated logic, inconsistent validation, shared mutable state, unclear ownership.
- Centralize the rule in one place (domain/use-case), add tests, and delete duplicates.
- Add a postmortem: what boundary or contract was missing?

---

### Juniors add code "where it works"

**Q:** Junior developers keep adding code in random places "where it works." How would you coach them and adjust the project structure to enforce good architectural boundaries?

**Key answers:**

- Provide a "where does this go?" guide and code templates for common additions.
- Set up review gates (owners per module) and CI rules that catch forbidden imports.
- Keep examples in-repo (one feature implemented "the right way").

---

## Iterative Architecture

### Feature-based packages → stricter layer separation

**Q:** The first version of your app used a simple "feature-based packages" structure, but three months later you want stricter separation of layers. How would you incrementally refactor towards a cleaner architecture while keeping the app shippable?

**Key answers:**

- Introduce layer folders inside one feature at a time (presentation/domain/data).
- Add interfaces at boundaries, move implementations behind them, and keep routing stable.
- Continuously ship by keeping changes small and covered by tests.

---

### New module — original architectural choice was wrong

**Q:** You introduce a new module and realize your original architectural choice for that module was wrong. How do you roll back or change direction with minimal disruption?

**Key answers:**

- Keep module API stable; change internals behind the interface.
- Use deprecation + migration path instead of a big-bang rewrite.
- If rollback is needed, keep both implementations temporarily and switch by configuration/flag.

---

## Simplicity vs. Complexity

### BLoC + Clean Architecture + custom DI for small internal tool

**Q:** A teammate proposes a very complex BLoC + Clean Architecture + custom DI setup for a small internal tool app. How would you evaluate this proposal and suggest a simpler alternative if appropriate?

**Key answers:**

- Evaluate by expected lifetime, team size, change rate, and risk.
- Suggest a simpler stack (e.g., Provider/Riverpod + repositories) with good testing, without heavy ceremony.
- Keep an "upgrade path" documented if the tool grows.

---

### When to introduce more abstraction

**Q:** In a critical feature with complex business rules, going too simple makes the code unreadable. How do you decide when it is worth introducing more abstraction?

**Key answers:**

- Introduce abstraction when it reduces duplication and clarifies intent (use-cases, rule objects, policies).
- Prefer explicit domain modeling over generic helpers.
- Add tests first; complexity without tests becomes unmaintainable.

---

## Architectural Styles

### Large app with clear domains (auth, catalog, payments)

**Q:** You are building a large app with clear domains (auth, catalog, payments). How would you apply a layered architecture and when would you consider splitting into modules or plugins?

**Key answers:**

- Use per-domain feature modules with internal layers; expose only public APIs between domains.
- Split into separate packages when compile times, ownership, or release cadence require it.
- Create shared "core" packages for networking, analytics, and design system.

---

### Chat app — many events (typing, message, delivery status)

**Q:** A chat application requires reacting to many events (typing, message received, delivery status). How would you leverage an event-driven style in your Flutter architecture to handle this?

**Key answers:**

- Model events as a stream and reduce them into state (event → reducer → new state).
- Use a single event pipeline per feature to avoid scattered subscriptions.
- Keep side effects (websocket, persistence) behind services/repositories.

---

### White-label / microkernel (plugin) style

**Q:** You are designing a core app that must be extended by different clients (white-label builds). How would you apply a microkernel (plug-in) style on the Flutter side?

**Key answers:**

- Define extension points (interfaces) for theming, feature toggles, and client-specific modules.
- Load client-specific implementations via DI + build-time flavors.
- Keep core stable and restrict what plugins can access.

---

## UI Architectures

### setState everywhere → introduce Provider/BLoC/Riverpod

**Q:** A medium app currently uses setState everywhere and has become hard to maintain. How would you choose and gradually introduce a state management architecture (e.g., Provider/BLoC/Riverpod) based on the team's skills and app complexity?

**Key answers:**

- Pick one approach and write a migration guideline; start with the most painful feature first.
- Keep setState for local ephemeral UI state, move cross-screen and async state into the chosen architecture.
- Add examples and enforce consistency in reviews.

---

### Clean Architecture with existing BLoC app

**Q:** You are asked to integrate Clean Architecture in an existing Flutter app with BLoC. How would you design the layers and manage communication between UI, use cases, and repositories?

**Key answers:**

- UI dispatches events to BLoC; BLoC calls use-cases; use-cases depend on repository interfaces; repositories implement remote/local sources.
- Keep mapping between DTO ↔ domain ↔ UI models explicit.
- Test: unit tests for use-cases and BLoCs; integration tests for repository behavior.

---

### High-risk feature with uncertain requirements

**Q:** You are working on a high-risk feature with uncertain requirements. How would you customize the architecture for just this module so that it is easy to experiment and later integrate into the main project?

**Key answers:**

- Isolate it as a feature module with clear boundaries and a thin public API.
- Allow faster iteration internally (simpler state shape), but keep adapters to domain contracts.
- Stabilize later by formalizing state/events and adding tests once requirements settle.
