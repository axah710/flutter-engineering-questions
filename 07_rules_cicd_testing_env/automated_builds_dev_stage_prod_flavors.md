# Automated builds for dev/stage/prod with flavors

**Q:** You need automated builds for dev/stage/prod with different flavors and environment configs. How would you design the CI/CD pipeline to handle this smoothly?

**Key answers:**

- Use Flutter flavors as per Flutter deployment docs for Android/iOS.
- Inject environment values with build-time config (e.g., --dart-define), and keep secrets in CI secret storage.
- Produce signed artifacts per flavor, and publish to separate tracks (internal testing / TestFlight groups).
