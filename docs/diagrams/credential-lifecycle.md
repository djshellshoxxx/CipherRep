# Credential lifecycle

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
stateDiagram-v2
  [*] --> Authorized
  Authorized --> Issued
  Issued --> Validated
  Validated --> Included
  Included --> Revoked
  Included --> Expired
  Included --> Superseded
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
