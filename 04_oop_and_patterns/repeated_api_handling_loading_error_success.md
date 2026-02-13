# Repeated API handling (loading, error, success)

**Q:** Your app has repeated code for handling API calls (loading, error, success), copy-pasted across screens. How would you use design patterns to centralize this logic and make it easier to evolve?

**Key answers:**

- Introduce a shared Result/Either type and a base async handler (or repository wrapper) that standardizes loading/error mapping.
- Use Repository + UseCase patterns: UI calls use-cases, gets typed results, and renders states consistently.
- Add shared retry/backoff and error translation in one layer.
