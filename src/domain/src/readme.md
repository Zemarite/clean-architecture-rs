# Domain Layer

The **Domain** project contains the core business logic of the application.

## Responsibilities

- **Entities**
  - that are related and should change together should be grouped into an Aggregate
  - should leverage encapsulation and should minimize public setters.
  - can leverage Domain Events to communicate changes to other parts of the system.
  - can define Specifications that can be used to query for them.
  
- **Value Objects** (immutable, equality by attributes) – src/domain/value_objects/
  - should be immutable and should implement equality based on their properties.
- **Repository Traits** (in src/domain/repositories/)
  - Traits defines the contract in pure domain language without any trace of databases, ORMs, HTTP clients, or frameworks
  - Raise events only from aggregate root methods.
  - Keep events lean — carry minimal data (IDs + facts).
  - Use correlation / causation IDs for distributed tracing.
  - Handle events idempotently (especially in eventual consistency).
  - Publish after commit (via UnitOfWork commit hook or explicit publish step).
  - Prefer enum of events over dyn DomainEvent when possible (better perf, exhaustiveness).
- **Domain Events**
- **Business rules and invariants**  

## Dependencies

- The Domain layer **must not depend on any other project**.
- It contains pure business logic only.

## Notes

This layer remains stable even if infrastructure, UI, or application code changes. It represents the heart of the system.
