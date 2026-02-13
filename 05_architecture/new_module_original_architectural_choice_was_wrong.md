# New module — original architectural choice was wrong

**Q:** You introduce a new module and realize your original architectural choice for that module was wrong. How do you roll back or change direction with minimal disruption?

**Key answers:**

- Keep module API stable; change internals behind the interface.
- Use deprecation + migration path instead of a big-bang rewrite.
- If rollback is needed, keep both implementations temporarily and switch by configuration/flag.
