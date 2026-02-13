# Complex multi-step animation

**Q:** You are asked to build a complex animation with multiple steps. The current approach is a large method that imperatively animates properties. How would you apply the "everything is a widget" idea to make this animation manageable?

**Key answers:**

- Split into animation widgets (one widget per step) and compose them (e.g., AnimatedSwitcher, FadeTransition, SlideTransition).
- Use AnimationController + TweenSequence for staged effects, and keep each animated part isolated.
- Wrap expensive animated regions in RepaintBoundary where appropriate.
