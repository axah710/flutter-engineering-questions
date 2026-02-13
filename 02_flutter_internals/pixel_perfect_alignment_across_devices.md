# Pixel-perfect alignment across devices

**Q:** A designer wants pixel-perfect alignment across devices, but you see layout behaving differently on rotation and resize. How do you use understanding of layout phases (constraints → layout → paint) to fix this?

**Key answers:**

- Diagnose constraints: check for unbounded constraints, wrong parent widgets, and "hardcoded sizes."
- Use LayoutBuilder, MediaQuery, AspectRatio, FittedBox, and responsive breakpoints to adapt to constraints.
- Ensure text scaling and safe areas are handled (don't "pixel perfect" by breaking accessibility).
