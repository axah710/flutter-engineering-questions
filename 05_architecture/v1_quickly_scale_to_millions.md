# V1 quickly but scale to millions

**Q:** A startup asks you to build a "v1" quickly but expects to scale to millions of users. How would you propose an architecture that allows fast development now but leaves room for serious evolution later?

**Key answers:**

- Start with feature-based structure + clear layers (UI/state, domain, data) but keep it lightweight.
- Establish interfaces early (repositories/services) so implementation can evolve without UI churn.
- Bake in observability (logging, crash reporting) and testing baseline from day one.
