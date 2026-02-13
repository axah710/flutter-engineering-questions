# Critical feature only in senior's head

**Q:** A critical feature exists only in one senior developer's head. When they go on vacation, nobody can fix a production bug. What documentation would you introduce and how would you keep it up to date?

**Key answers:**

- Add runbooks (how to debug/operate), ADRs (why decisions were made), and a short architecture overview.
- Document critical flows with sequence diagrams and "failure modes" (what breaks, how to recover).
- Keep docs close to code and require doc updates in PRs that change behavior.
