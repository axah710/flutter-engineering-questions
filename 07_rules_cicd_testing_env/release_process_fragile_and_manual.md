# Release process fragile and manual

**Q:** The release process is fragile and manual, causing last-minute mistakes. How would you use CI/CD plus flavors to create a reliable, repeatable release pipeline?

**Key answers:**

- CI builds signed artifacts per flavor, runs tests, and tags releases automatically.
- Separate approval steps (manual promote) from build steps (automated) to reduce human error.
- Use staged rollout and monitoring gates (crash-free sessions, key metrics).
