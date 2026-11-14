# Privacy boundaries

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
flowchart LR
  A[Rater] -->|Encrypted rating| B[Aggregator]
  B -->|Authenticated aggregate| C[Holder]
  C -->|ZK proof| D[Verifier]
  E[Issuer registry] -->|Trust policy| D
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
