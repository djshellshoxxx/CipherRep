# Deployment topology

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
flowchart TD
  P[CipherRep interoperable protocol] --> A[Single-operator deployment]
  P --> B[Federated issuers]
  P --> C[Threshold-operated aggregation]
  P --> D[Independent local verifier]
  A --> D
  B --> D
  C --> D
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
