# Encrypted aggregation sequence

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
sequenceDiagram
  participant R as Rater
  participant V as Validator
  participant A as Aggregator
  participant S as Snapshot
  R->>V: Signed credential and encrypted rating
  V->>V: Check eligibility, bounds and uniqueness
  V->>S: Commit valid contribution
  S->>A: Authenticated eligible ciphertext set
  A->>A: Homomorphic sum
  A->>S: Bind aggregate to snapshot
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
