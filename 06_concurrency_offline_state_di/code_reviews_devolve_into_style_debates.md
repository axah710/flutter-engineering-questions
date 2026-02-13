# Code reviews devolve into style debates

**Q:** Code reviews in your team often devolve into style debates. How would you design and implement a linting rule set (analysis_options) to enforce style and catch common issues automatically?

**Key answers:**

- Adopt a standard baseline (Flutter/Dart recommended lints) and add only rules that prevent real bugs.
- Encode architecture rules where possible (forbidden imports, layer boundaries) using lint tooling.
- Make CI fail on lint/format issues; code review focuses on design, not whitespace.
