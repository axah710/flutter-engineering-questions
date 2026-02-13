# Sensitive tokens logged in debug builds

**Q:** After a security review, you learn that sensitive tokens are being logged in debug builds. Describe how you would clean this up and prevent similar issues in the future.

**Key answers:**

- Remove sensitive logs immediately and add automated log redaction in the logging layer.
- Add lint/code review rules: never log secrets; gate release builds with checks.
- Verify crash reporting scrubs PII and tokens.
