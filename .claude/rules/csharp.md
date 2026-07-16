---
paths:
  - "**/*.cs"
  - "**/*.csproj"
---

# C# Engineering Rules

## Language

- Target the repository-defined .NET and C# versions.
- Do not introduce compatibility patterns for unsupported framework versions.
- Enable nullable reference types.
- Prefer file-scoped namespaces.
- Prefer records only for genuinely value-oriented data.
- Do not use exceptions for expected control flow.

## Async

- Async methods must accept CancellationToken when cancellation is meaningful.
- Never use async void except event handlers.
- Do not block asynchronous code with .Result, .Wait(), or GetAwaiter().GetResult().
- Propagate CancellationToken through every asynchronous boundary.

## Domain Design

- Keep domain models independent of EF Core, ASP.NET Core, serialization, and transport concerns.
- Do not expose EF Core entities directly through APIs.
- Enforce invariants inside aggregate boundaries.
- Use value objects for concepts with validation or domain behavior.

## Dependency Injection

- Prefer constructor injection.
- Do not resolve services through IServiceProvider in application code.
- Avoid service locator patterns.
- Keep registration in composition roots.

## Testing

- Test behavior, not implementation details.
- Use integration tests for persistence, serialization, and framework boundaries.
- Avoid mocking value objects and pure domain services.
