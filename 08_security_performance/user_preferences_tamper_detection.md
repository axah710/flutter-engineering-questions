# User preferences — tamper detection

**Q:** You need to store user preferences locally and verify they have not been tampered with. Explain how you would combine hashing and/or digital signatures to achieve this.

**Key answers:**

- For tamper detection, store (data + HMAC) using a secret key stored in secure storage; verify on read.
- If you need non-repudiation or server-verifiable integrity, use digital signatures (private key signs, public key verifies).
- Use authenticated encryption modes (e.g., GCM) when confidentiality + integrity are both required.
