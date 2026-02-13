# get_it (with or without injectable) — avoid "global God container"

**Q:** You decide to use get_it (with or without injectable) in a large project. How would you organize registration, lifecycles (singleton vs factory), and environment-specific dependencies to avoid a "global God container"?

**Key answers:**

- Register per feature/module (each module exposes a register()), and keep the root only orchestrating module registration.
- Use singleton for stateless/shared services, factory for short-lived objects (BLoCs/ViewModels), and scoped lifetimes for flows.
- Bind environment-specific implementations (dev/stage/prod) via configuration and keep selection logic out of UI.
