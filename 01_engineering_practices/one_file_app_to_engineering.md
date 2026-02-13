# One-file app → engineering

**Q:** You inherit a Flutter app where everything is in one file and "works," but adding features always breaks something else. How would you show the team the difference between "just programming" and engineering, and what concrete changes would you introduce?

**Key answers:**

- Show failure modes: no boundaries, no tests, no contracts, no observability → changes cause regressions.
- Introduce modules and contracts: feature folders, repositories, use-cases, DTO/domain separation, and a consistent state management approach.
- Add quality loops: test pyramid, CI gating, code review checklist, and measurable goals (crash-free %, build time, test time).
