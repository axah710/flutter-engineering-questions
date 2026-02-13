# Bug keeps reappearing in different modules

**Q:** A bug keeps reappearing in different modules, suggesting a systemic design problem. How would you use an architectural mindset to identify root causes instead of just patching each bug?

**Key answers:**

- Look for common causes: duplicated logic, inconsistent validation, shared mutable state, unclear ownership.
- Centralize the rule in one place (domain/use-case), add tests, and delete duplicates.
- Add a postmortem: what boundary or contract was missing?
