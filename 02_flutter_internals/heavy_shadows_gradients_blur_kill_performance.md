# Heavy shadows, gradients, blur kill performance

**Q:** The design team wants heavy shadows, gradients, and blur on multiple layers. The first implementation looks good but kills performance. What rendering optimizations would you apply to keep it visually appealing but smooth?

**Key answers:**

- Reduce blur radius and the number of layers with filters; prefer simpler shadows or baked assets.
- Avoid animating blurred widgets; animate transforms/opacity instead.
- Isolate expensive areas with RepaintBoundary and flatten the widget tree where possible.
