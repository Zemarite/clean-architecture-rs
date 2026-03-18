# Repositories

Repository is not a concrete class but is typically expressed as a trait defined in the domain layer (or sometimes in a shared ports / interfaces module within a clean/hexagonal architecture).
This follows the core DDD principle: repositories belong to the domain, but their implementations live in the infrastructure layer. The trait acts as a port — it defines the contract in pure domain language without any trace of databases, ORMs, HTTP clients, or frameworks.
