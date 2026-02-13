# New app: small team, complex domain, deadline, offline, multi-platform

**Q:** You are designing a new Flutter app with: small team, complex domain, strict deadline, offline mode, and multiple platforms. How would these constraints influence your architectural choice and why?

**Key answers:**

- Small team + deadline: keep framework choices minimal; choose one state management approach and one DI approach.
- Complex domain + offline: invest in strong domain/data boundaries, repositories, and a sync layer.
- Multi-platform: avoid platform-specific leakage into UI; isolate platform integrations behind services.
