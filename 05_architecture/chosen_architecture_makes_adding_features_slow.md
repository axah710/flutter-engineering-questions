# Chosen architecture makes adding features slow

**Q:** Mid-project, the team realizes the chosen architecture makes adding new features extremely slow. How would you guide an incremental architectural change without stopping feature work?

**Key answers:**

- Identify pain points and define a target architecture (what changes, what stays).
- Migrate incrementally by routing new work through the new boundaries and wrapping old modules with adapters.
- Track progress with a "migration board" and enforce rules (new code must follow target structure).
