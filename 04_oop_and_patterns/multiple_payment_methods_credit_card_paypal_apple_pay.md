# Multiple payment methods (credit card, PayPal, Apple Pay)

**Q:** Your app supports multiple payment methods (credit card, PayPal, Apple Pay) and more may be added later. How would you design the behavior so adding a new method does not require touching existing business logic?

**Key answers:**

- Use Strategy: PaymentMethod interface with pay(); select strategy at runtime.
- Keep shared validation and error mapping in a coordinator/service.
- Add integration tests per payment strategy.
