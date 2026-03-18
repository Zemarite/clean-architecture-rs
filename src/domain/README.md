# Domain Layer

The **Domain** project contains the core business logic of the application.

## Responsibilities

- **Entities** representing core business objects (e.g., Order, User, Product)
- **Value Objects** representing immutable concepts (e.g., Money, EmailAddress)
- **Repository Traits** defining contracts for data access (e.g., OrderRepository, UserRepository)
- **Enums** representing domain concepts (e.g., OrderStatus, UserRole)
- **Errors** representing domain-specific failure cases (e.g., InsufficientFunds, InvalidEmail)
- **Domain Events** representing significant occurrences within the domain (e.g., OrderPlaced, UserRegistered)
- **Business rules and invariants** enforced within entities and value objects  

## Dependencies

- The Domain layer **must not depend on any other project**.
- It contains pure business logic only.

## Notes

This layer remains stable even if infrastructure, UI, or application code changes. It represents the heart of the system.
