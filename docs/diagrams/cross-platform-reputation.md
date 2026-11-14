# Cross-platform reputation

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
flowchart TD
  A[Marketplace A] --> C[CipherRep credential ecosystem]
  B[Marketplace B] --> C
  C --> D[User private reputation proof]
  D --> E[Escrow platform]
  D --> F[Freelancing platform]
  D --> G[P2P marketplace]
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
