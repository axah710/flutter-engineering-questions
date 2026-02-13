# OOP, SOLID & Design Patterns

## OOP Analysis

### User class with UI, networking, persistence mixed

**Q:** In your project, a "User" class has fields and methods related to UI, networking, and persistence all together. Explain how you'd analyze this design and refactor it using OOP concepts to separate responsibilities.

**Key answers:**

- Split by responsibility: User (domain entity), UserDto (API mapping), UserRepository (data access), UserViewModel (UI state).
- Apply encapsulation: keep invariants in the domain entity; keep serialization/parsing outside.
- Reduce coupling by introducing interfaces for repositories/services and injecting them.

---

### Deep inheritance hierarchy

**Q:** You see a deep inheritance hierarchy (BaseWidget → AppWidget → SpecialWidget → SpecialWidgetWithLogging). How would you restructure this using composition to make it easier to maintain?

**Key answers:**

- Replace inheritance with composable widgets and decorators (e.g., wrap a widget with a logging wrapper).
- Extract cross-cutting concerns (logging, analytics, theming) into wrappers/mixins only when truly necessary.
- Prefer small widgets + shared utilities over "god base classes."

---

## Implementing Classic Software Principles (SOLID)

### Service does API + JSON parsing into UI models

**Q:** A service class in your Flutter app both calls APIs and parses JSON into UI models. Bugs appear often after small changes. How would you apply SOLID principles to split and reorganize this code?

**Key answers:**

- Single Responsibility: separate API client, DTO parser/mapper, repository, and UI model mapping.
- Open/Closed: add new endpoints by adding new DTO + mapper, not by modifying existing unrelated code.
- Dependency Inversion: depend on interfaces (e.g., UserDataSource) rather than concrete HTTP clients.

---

### Adding offline caching (Dependency Inversion)

**Q:** You need to add offline caching to an existing data layer. How would you apply the Dependency Inversion Principle so that the UI is not directly dependent on details of local or remote storage?

**Key answers:**

- Define repository interfaces used by UI/use-cases; implement with RemoteDataSource + LocalCacheDataSource.
- Choose caching strategy (cache-aside, write-through) inside repository, not UI.
- Make storage swappable via DI (mock/in-memory for tests, SQLite/Isar for prod).

---

## Role of Design Patterns

### Repeated API handling (loading, error, success)

**Q:** Your app has repeated code for handling API calls (loading, error, success), copy-pasted across screens. How would you use design patterns to centralize this logic and make it easier to evolve?

**Key answers:**

- Introduce a shared Result/Either type and a base async handler (or repository wrapper) that standardizes loading/error mapping.
- Use Repository + UseCase patterns: UI calls use-cases, gets typed results, and renders states consistently.
- Add shared retry/backoff and error translation in one layer.

---

### "Adding patterns everywhere" for enterprise look

**Q:** A junior suggests "adding patterns everywhere" to look "enterprise-grade." Given a relatively simple app, how would you decide which patterns to use and which to avoid?

**Key answers:**

- Choose patterns only when they reduce real pain (duplication, tight coupling, hard testing).
- Keep a small "approved patterns" list and require justification for new frameworks/abstractions.
- Prefer the simplest thing that keeps code readable and testable.

---

## Creational Patterns

### Multiple themes (light/dark/custom)

**Q:** Your app must support multiple themes (light/dark/custom) and you want to keep theme creation consistent. How would you use a creational pattern to manage this?

**Key answers:**

- Use a Factory/Builder to generate ThemeData from a small config (brand colors, typography).
- Keep theme tokens in one place; avoid scattering colors across widgets.
- Provide theme variants by environment/flavor and runtime user preference.

---

### Multiple network client variants (mock, real, logging)

**Q:** You have multiple ways to create a network client (mock, real, logging). How would you design a factory that decides which one to provide based on environment?

**Key answers:**

- Build a HttpClientFactory that selects implementation based on environment config (dev/stage/prod) and debug flags.
- Keep selection logic out of UI; do it in DI registration.
- Ensure consistent interceptors (auth, retry) across variants.

---

## Structural Patterns

### Third-party REST API JSON doesn't match domain model

**Q:** You integrate a third-party REST API whose JSON does not match your app's domain model. How would you use a structural pattern to shield your code from this mismatch?

**Key answers:**

- Use Adapter + Mapper: convert API DTOs to domain entities in a dedicated layer.
- Keep third-party schema changes contained to DTO/mappers.
- Add contract tests for mapping.

---

### God widget with huge build method

**Q:** A legacy screen uses a heavy "God widget" with a huge build method. How would you apply structural patterns to break it into reusable pieces without changing behavior?

**Key answers:**

- Use Composite: extract subtrees into widgets with clear inputs.
- Use Presenter/ViewModel to move logic out of build.
- Add golden/widget tests before refactoring to lock down behavior.

---

## Behavioral Patterns

### Multiple payment methods (credit card, PayPal, Apple Pay)

**Q:** Your app supports multiple payment methods (credit card, PayPal, Apple Pay) and more may be added later. How would you design the behavior so adding a new method does not require touching existing business logic?

**Key answers:**

- Use Strategy: PaymentMethod interface with pay(); select strategy at runtime.
- Keep shared validation and error mapping in a coordinator/service.
- Add integration tests per payment strategy.

---

### Multiple widgets react to same global events (e.g. logout)

**Q:** You have multiple widgets that need to react to the same global events (e.g., user logged out). How do you structure this using a behavioral pattern so it remains testable?

**Key answers:**

- Use Observer (event bus/store) with typed events; widgets subscribe via state management layer, not via static globals.
- Make the event source injectable so tests can trigger events deterministically.
- Ensure subscriptions are lifecycle-safe (auto-dispose on route exit).
