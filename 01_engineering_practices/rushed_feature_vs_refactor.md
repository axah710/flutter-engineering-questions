# Rushed feature vs refactor

**Q:** Management wants a new feature rushed in three days, but implementing it properly requires refactoring a core module. How do you communicate and justify an engineering-oriented approach while still being realistic about deadlines?

**Key answers:**

- Present options with risk/impact: (A) fast patch with known risks + explicit follow-up, (B) refactor+feature with staged delivery.
- Propose a thin vertical slice that doesn't worsen the core module (wrap old code with an adapter, implement new code behind interface).
- Negotiate scope: deliver must-have behavior now, postpone "nice-to-have" UI polish.
