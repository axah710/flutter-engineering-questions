# Animation drops frames when heavy calculation runs

**Q:** An animation drops frames when a heavy calculation runs. What would you do to separate UI rendering from computation?

**Key answers:**

- Offload computation to an isolate (no shared memory; message passing).
- Reduce per-frame work: precompute, memoize, and avoid rebuilding large subtrees during animation.
- Use RepaintBoundary to isolate repaints.
