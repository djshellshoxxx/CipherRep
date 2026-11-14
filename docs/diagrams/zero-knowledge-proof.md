# Zero-knowledge proof lifecycle

> Conceptual workflow only. Exact protocol semantics, security properties and deployment choices remain undecided.

```mermaid
sequenceDiagram
  participant V as Verifier
  participant H as Holder
  participant P as Prover
  V->>H: Policy and audience challenge
  H->>P: Authorized witness and snapshot inputs
  P->>P: Prove threshold and integrity
  P-->>H: Proof
  H->>V: Presentation
  V->>V: Check proof, trust and freshness
```

See [protocol specification](../../spec/protocol.md), [architecture](../../ARCHITECTURE.md), and [trust model](../../spec/trust-model.md).
