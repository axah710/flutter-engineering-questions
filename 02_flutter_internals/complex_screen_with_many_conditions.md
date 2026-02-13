# Complex screen with many conditions

**Q:** A complex screen has many conditions for what to show. Right now it is built with many if/else inside the build method. How do you redesign it using Flutter's core principles to make it easier to reason about and change?

**Key answers:**

- Model the screen as explicit UI states (e.g., loading/empty/error/ready, plus sub-states) using sealed classes/unions.
- Map state → widget in one place (a small "renderer" function), and extract each branch into its own widget.
- Push decision-making earlier: compute "view data" from domain models before build, so build stays mostly layout.
