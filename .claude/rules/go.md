---
paths:
  - "**/*.go"
  - "**/go.mod"
  - "**/go.sum"
---

# Go Engineering Rules

## Idiomatic Go

- Prefer simple concrete types over speculative abstractions.
- Define interfaces at the consumer boundary, not the implementation package.
- Keep interfaces small and behavior-oriented.
- Do not introduce Java-style repositories, factories, builders, or dependency injection containers without a demonstrated need.
- Accept interfaces and return concrete types unless the API requires otherwise.

## Errors

- Return errors explicitly.
- Wrap errors with context using %w when callers may inspect the cause.
- Use errors.Is and errors.As instead of string matching.
- Do not log and return the same error at the same abstraction boundary.
- Panic only for unrecoverable programmer errors or impossible initialization states.

## Context

- Pass context.Context as the first parameter.
- Do not store Context in structs.
- Do not pass nil Context.
- Propagate cancellation and deadlines through I/O boundaries.

## Concurrency

- Do not start goroutines without defining ownership, cancellation, and shutdown behavior.
- Avoid unbounded goroutine creation.
- The goroutine that creates a channel should normally own closing it.
- Never close a channel from the receiver side.
- Prefer synchronous code unless concurrency provides a concrete benefit.

## Packages

- Keep package names short, lowercase, and free of stutter.
- Avoid generic package names such as utils, helpers, common, or shared.
- Keep internal implementation under internal/ where appropriate.
- Avoid cyclic conceptual dependencies even when import cycles do not yet exist.

## Testing

- Prefer table-driven tests when cases share structure.
- Mark reusable test helpers with t.Helper().
- Use httptest and real serialization boundaries for HTTP tests.
- Run tests with the race detector for concurrent code.
