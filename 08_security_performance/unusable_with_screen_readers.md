# Unusable with screen readers

**Q:** QA reports that the app is almost unusable with screen readers. How would you go through a key screen and improve semantics, focus order, and labels using Flutter tools?

**Key answers:**

- Add semantic labels/roles for tappable elements, merge semantics where appropriate, and ensure logical traversal order.
- Fix focus management for dialogs/sheets and ensure keyboard navigation works.
- Add accessibility tests/checklists to PR reviews.
