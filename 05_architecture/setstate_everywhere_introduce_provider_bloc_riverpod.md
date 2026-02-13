# setState everywhere → introduce Provider/BLoC/Riverpod

**Q:** A medium app currently uses setState everywhere and has become hard to maintain. How would you choose and gradually introduce a state management architecture (e.g., Provider/BLoC/Riverpod) based on the team's skills and app complexity?

**Key answers:**

- Pick one approach and write a migration guideline; start with the most painful feature first.
- Keep setState for local ephemeral UI state, move cross-screen and async state into the chosen architecture.
- Add examples and enforce consistency in reviews.
