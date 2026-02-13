# New developer bypasses formatting and analysis

**Q:** A new developer pushes code that bypasses formatting and analysis. How would you use tooling (pre-commit hooks, CI) to enforce rules without relying on manual policing?

**Key answers:**

- Add pre-commit hooks for dart format + flutter analyze + unit tests.
- CI is the final gate: fail builds if formatting or analysis differs.
- Provide "one command" scripts (makefile/task runner) so compliance is easy.
