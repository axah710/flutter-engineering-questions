# WebAssembly and client technology

**Q:** A backend team wants to expose features via WebAssembly in the future. How would you argue for or against Flutter as the main client technology in this evolving ecosystem?

**Key answers:**

- Treat WebAssembly as an implementation detail for compute-heavy logic; clients still need UI, state, storage, and platform integrations.
- If shared core logic is needed across platforms, consider: Dart-only shared logic, or WASM for specific algorithms with clear boundaries.
- Decide based on integration cost: if WASM becomes critical everywhere (including web), ensure the chosen client stack can call it cleanly (via FFI on native, JS interop on web).
