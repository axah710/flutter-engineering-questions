# Complex animation repaints entire screen

**Q:** You notice that a complex animation causes the entire screen to repaint, not just the changing part. How would you apply RepaintBoundary and other tricks to optimize this?

**Key answers:**

- Wrap the animated region with RepaintBoundary to isolate repaints.
- Reduce the animated subtree size and avoid triggering layout changes during animation.
- Prefer transform/opacity animations over re-layout heavy changes.
