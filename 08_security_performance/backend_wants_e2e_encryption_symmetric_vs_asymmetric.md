# Backend wants E2E encryption — symmetric vs asymmetric

**Q:** The backend team wants the app to encrypt certain payloads end-to-end. How would you choose between symmetric and asymmetric encryption in this scenario?

**Key answers:**

- Use asymmetric crypto for key exchange/identity, symmetric crypto for bulk payloads (performance).
- Manage keys with a well-defined rotation and revocation strategy.
- Prefer standard, audited protocols over custom designs.
