# Reputation snapshot state machine

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
stateDiagram-v2
  [*] --> Collecting
  Collecting --> Committed
  Committed --> Active
  Active --> Superseded
  Active --> Disputed
  Disputed --> Corrected
  Corrected --> Superseded
  Active --> Expired
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
