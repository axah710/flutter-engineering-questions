# Banking feature — view transactions offline, sensitive ops online

**Q:** You are building a banking feature where users can view transactions offline but sensitive operations require connectivity. How would you apply security principles and OWASP guidance to design storage, encryption, and session handling?

**Key answers:**

- Store tokens securely and handle expiration; require re-auth for sensitive operations (OWASP mobile guidance).
- Encrypt sensitive offline data with authenticated encryption (GCM/CCM recommended).
- Separate "view-only offline" from "online-required actions" with server-side authorization and short session lifetimes.
