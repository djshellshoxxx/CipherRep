# Key lifecycle

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
stateDiagram-v2
  [*] --> Generated
  Generated --> Distributed
  Distributed --> Active
  Active --> Rotating
  Rotating --> Active
  Active --> Compromised
  Compromised --> Revoked
  Revoked --> Recovered
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
