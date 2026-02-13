# God widget with huge build method

**Q:** A legacy screen uses a heavy "God widget" with a huge build method. How would you apply structural patterns to break it into reusable pieces without changing behavior?

**Key answers:**

- Use Composite: extract subtrees into widgets with clear inputs.
- Use Presenter/ViewModel to move logic out of build.
- Add golden/widget tests before refactoring to lock down behavior.
