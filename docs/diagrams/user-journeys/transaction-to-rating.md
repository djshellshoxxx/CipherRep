# Transaction to rating

> **Conceptual diagram — implementation-independent.** This is intended behavior, not a claim that cryptographic construction or deployment choices have been finalized.

```mermaid
sequenceDiagram
 participant U as 👤 Buyer
 participant M as 🏪 Marketplace
 participant S as 👤 Seller
 participant R as 🔒 Rating service
 U->>M: Complete transaction
 S->>M: Confirm eligible event
 M-->>U: One-use rating authorization
 U->>R: Signed rating credential and encrypted contribution
 R->>R: Validate eligibility and uniqueness
 R-->>M: Inclusion status (no rating plaintext)
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
