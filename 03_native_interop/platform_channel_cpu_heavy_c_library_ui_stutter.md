# Platform channel + CPU-heavy C library causes UI stutter

**Q:** A previous developer uses platform channels to call a CPU-heavy C library. The UI stutters badly. How would you propose moving this to FFI and isolates to fix the problem?

**Key answers:**

- Replace repeated channel roundtrips with direct FFI calls for high-frequency compute.
- Run compute in a worker isolate so UI isolate stays responsive; isolates have isolated memory and message passing.
- Benchmark before/after (time per frame, CPU, battery), and keep a fallback path if native lib fails to load.
