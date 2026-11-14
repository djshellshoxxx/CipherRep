# Cryptographic architecture

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
flowchart TD
  A[Authenticated rating] --> B[Rating commitment]
  A --> C[Homomorphic encryption]
  B --> D[Authenticated rating set]
  C --> E[Encrypted aggregation]
  D --> F[Aggregate integrity proof]
  E --> F
  F --> G[ZK threshold proof]
  G --> H[Independent verification]
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
