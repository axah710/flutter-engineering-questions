# Large C API — hundreds of functions

**Q:** Your team wants to expose a large C API (hundreds of functions) to Flutter, and manually writing bindings is error-prone. Describe how you'd set up FFIgen in this project and how you'd keep the generated code in sync with the native library over time.

**Key answers:**

- Add ffigen config (headers, output, naming), generate bindings into a dedicated generated/ folder, and never hand-edit generated files.
- Pin native library versions and regenerate bindings as part of CI (or a controlled build step).
- Add compile-time + smoke tests that call a small subset of functions to detect breaking changes early.
