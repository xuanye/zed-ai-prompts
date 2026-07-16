---
paths:
  - "**/*.ts"
  - "**/*.tsx"
---

# React and TypeScript Engineering Rules

## TypeScript

- Keep strict type checking enabled.
- Do not use any. Use unknown and narrow it explicitly.
- Do not use non-null assertions unless an invariant is externally guaranteed and documented.
- Prefer discriminated unions for state with mutually exclusive variants.
- Model invalid states so they are unrepresentable.
- Prefer type inference for local values; annotate public boundaries.
- Do not duplicate runtime schemas and static types when schema inference is available.
- Avoid enums unless interoperability requires them; prefer const objects or literal unions.

## React Components

- Use function components.
- Components and Hooks must remain pure.
- Keep rendering logic declarative.
- Do not mutate props, state, query data, or external stores.
- Prefer composition over boolean-heavy configurable components.
- Split components by responsibility, not arbitrary line count.
- Do not create wrapper components that add no semantic or behavioral value.

## State

- Keep state as local as possible.
- Do not store derived values in state.
- Compute inexpensive derived data during rendering.
- Use reducers for state transitions with multiple related events.
- Use server-state libraries for remote data; do not duplicate server state in client stores.
- Global stores must represent genuinely shared application state.

## Effects

- Use effects only to synchronize with systems outside React.
- Do not use effects to derive state from props or other state.
- Every subscription, timer, observer, and event listener must have deterministic cleanup.
- Do not suppress exhaustive-deps warnings without documenting the invariant.
- Prefer event handlers over effects for user-triggered behavior.

## Hooks

- Call Hooks only at the top level of components and custom Hooks.
- Custom Hooks must encapsulate reusable stateful behavior, not merely rename utility functions.
- Hooks must expose a narrow, stable API.
- Avoid returning large unstructured objects from Hooks.

## Data and Boundaries

- Validate untrusted data at I/O boundaries.
- Keep API transport models separate from UI view models when their semantics differ.
- Do not access fetch directly throughout components; centralize transport behavior.
- Represent loading, success, empty, and failure states explicitly.

## Testing

- Test behavior through accessible user interactions.
- Prefer semantic queries over test IDs.
- Do not assert implementation details such as internal state or Hook calls.
- Use unit tests for pure logic, component tests for interaction, and E2E tests for critical workflows.
