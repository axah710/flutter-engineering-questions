# ML model 300 ms per inference on device

**Q:** A machine-learning model must run entirely on device and takes 300 ms per inference. How would you use isolates to integrate this without making the UI stutter?

**Key answers:**

- Run inference off the UI isolate and return results via messages; isolates don't share state.
- Batch requests and drop stale requests (only latest inference matters for some UIs).
- Warm up model and cache resources to reduce spikes.
