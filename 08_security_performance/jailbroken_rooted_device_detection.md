# Jailbroken/rooted device detection

**Q:** You are asked to add jailbroken/rooted device detection. How would you implement it in Flutter and what would the app do when such a device is detected?

**Key answers:**

- Use a platform plugin/service that performs detection with best-effort signals (never 100% reliable).
- Respond with risk-based controls: block sensitive operations, require step-up auth, and show a clear warning.
- Log only non-sensitive security events for monitoring.
