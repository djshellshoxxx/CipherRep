# Protocol message flow

> **Conceptual diagram — implementation-independent.** This is intended behavior, not a claim that cryptographic construction or deployment choices have been finalized.

```mermaid
sequenceDiagram
 participant I as 🏪 Issuer
 participant R as 👤 Rater
 participant A as 🔒 Aggregator
 participant H as 👤 Holder
 participant V as 🛡️ Verifier
 I-->>R: Eligibility authorization
 R->>A: Signed credential and encrypted contribution
 A->>A: Validate and commit eligible set
 A-->>H: Authenticated snapshot and proof inputs
 V->>H: Presentation request
 H-->>V: Audience-bound ZK presentation
 V->>V: Independent verification
```

## Visual legend

- 👤 Individual user, rater or holder
- 🏪 Marketplace or issuer
- 👥 Group or organization
- 🤝 Escrow or trading service
- 🔒 Encrypted or privacy-sensitive computation
- 🗂️ Authenticated data or snapshot
- 🛡️ Independent verifier or security check
- 📜 Specification or policy
- 🧪 Testing and conformance
- 👩‍💻 Developer
- ⚙️ Configuration or compatibility
- ✅ Accepted / ❌ Rejected / ❔ Indeterminate

Icons are **generic visual cues**, not claims of a specific UI, algorithm, trust model or deployed service. Emoji rendering varies by platform; labels remain readable without the pictograms.


See [protocol](../../../spec/protocol.md), [implementation plan](../../../PLAN.md), and [decision register](../../decision-register.md). For exact normative semantics, defer to the finalized versioned protocol and its conformance tests.
