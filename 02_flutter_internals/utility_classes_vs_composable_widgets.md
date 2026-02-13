# Utility classes vs composable widgets

**Q:** On a project, developers often create "utility classes" that manipulate UI elements directly instead of composing widgets. This leads to duplicated logic and weird bugs. Using "everything is a widget," how would you refactor a specific example like a reusable card with actions?

**Key answers:**

- Create a ReusableActionCard widget that takes data + callbacks; keep it pure and composable.
- Extract sub-widgets: header, body, actions row; accept slot widgets for customization.
- Move "utility" logic into helpers that return widgets (or into theme/extensions), not imperative UI mutations.
