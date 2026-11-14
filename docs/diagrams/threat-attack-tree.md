# Threat and attack tree

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
flowchart TD
  A[Attack accepted reputation claim] --> B[Forge inputs]
  A --> C[Omit negatives]
  A --> D[Exploit proof verifier]
  A --> E[Replay stale proof]
  A --> F[Collude with custodians]
  B --> G[Issuer forgery or Sybil]
  C --> H[Incomplete snapshot]
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
