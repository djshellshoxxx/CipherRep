# Language-neutral architecture

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
flowchart TD
  A[CipherRep Protocol Specification] --> B[Rust Reference Implementation]
  A --> C[Independent Implementations]
  B --> D[WebAssembly and TypeScript]
  B --> E[Python Go and C ABI]
  B --> F[Swift Kotlin and C Sharp]
  A --> G[Shared Conformance Tests]
  C --> G
  D --> G
  E --> G
  F --> G
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
