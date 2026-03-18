# Repositories (in Rust)

In **Domain-Driven Design (DDD)** implemented in **Rust**, the **Repository** is not a concrete class but is typically expressed as a **trait** defined in the **domain layer** (or sometimes in a shared `ports` / `interfaces` module within a clean/hexagonal architecture).

This follows the core DDD principle: **repositories belong to the domain**, but their *implementations* live in the **infrastructure layer**. The trait acts as a **port** — it defines the contract in pure domain language without any trace of databases, ORMs, HTTP clients, or frameworks.

## Core Principles of a DDD Repository

A good repository trait in DDD should:

- Work with **whole aggregates** (not single entities or partial data)
- Use **domain types** in signatures (not primitives or DTOs)
- Return `Result<T, DomainError>` (or a custom error enum)
- Be **minimalistic** — only methods the domain actually needs
- Avoid generic CRUD explosion (no `findAll`, `deleteById`, etc. unless truly needed by the business)
- Often be **aggregate-specific** (one trait per aggregate root)

## Best Practices & Common Patterns

- **One trait per aggregate root** — `OrderRepository`, `CustomerRepository`, etc.
- **Generic over error** — Some teams use `trait OrderRepository<E>` (more flexible, more complex)
- **Unit-of-Work pattern** — For multiple aggregates in one transaction, many teams introduce a `UnitOfWork` trait or pass a transaction handle
- **Dynamic dispatch** — `Arc<dyn OrderRepository>` is very common in Axum / actix-web apps
- **Static dispatch** (generic) — Preferred when possible (better performance, better error messages)
  
Further reading / inspiration:

- Evans' *Domain-Driven Design* (blue book) – chapters 5 & 6
- Vernon’s *Implementing Domain-Driven Design*
