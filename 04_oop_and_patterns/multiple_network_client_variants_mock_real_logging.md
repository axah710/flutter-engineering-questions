# Multiple network client variants (mock, real, logging)

**Q:** You have multiple ways to create a network client (mock, real, logging). How would you design a factory that decides which one to provide based on environment?

**Key answers:**

- Build a HttpClientFactory that selects implementation based on environment config (dev/stage/prod) and debug flags.
- Keep selection logic out of UI; do it in DI registration.
- Ensure consistent interceptors (auth, retry) across variants.
