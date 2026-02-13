# Feature-based packages → stricter layer separation

**Q:** The first version of your app used a simple "feature-based packages" structure, but three months later you want stricter separation of layers. How would you incrementally refactor towards a cleaner architecture while keeping the app shippable?

**Key answers:**

- Introduce layer folders inside one feature at a time (presentation/domain/data).
- Add interfaces at boundaries, move implementations behind them, and keep routing stable.
- Continuously ship by keeping changes small and covered by tests.
