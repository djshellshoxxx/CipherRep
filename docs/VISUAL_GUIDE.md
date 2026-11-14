# CipherRep visual guide

The diagrams use Mermaid so GitHub renders them inline and contributors can edit them as text. **Every diagram is conceptual**, and no diagram selects an encryption scheme, zero-knowledge backend, custody arrangement or issuer admission model.

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


## Diagram library

### user journeys
- [End-to-end user journey](diagrams/user-journeys/end-to-end.md)
- [Transaction to rating](diagrams/user-journeys/transaction-to-rating.md)
- [Cross-platform reputation portability](diagrams/user-journeys/cross-platform-portability.md)

### developer
- [First-time developer integration](diagrams/developer/first-integration.md)
- [SDK initialization](diagrams/developer/sdk-initialization.md)
- [Offline verification](diagrams/developer/offline-verification.md)

### protocol
- [Protocol message flow](diagrams/protocol/message-flow.md)
- [Credential validation pipeline](diagrams/protocol/credential-validation.md)
- [Proof request and response](diagrams/protocol/proof-request-response.md)
- [Verification decision tree](diagrams/protocol/verification-decision-tree.md)
- [Reputation score calculation](diagrams/protocol/score-calculation.md)
- [Protocol version negotiation](diagrams/protocol/version-negotiation.md)
- [Error handling and recovery](diagrams/protocol/error-recovery.md)

### privacy
- [Data visibility by role](diagrams/privacy/data-visibility.md)
- [Multi-issuer reputation](diagrams/privacy/multi-issuer-reputation.md)
- [Conventional versus private reputation](diagrams/privacy/disclosure-comparison.md)

### development
- [Cross-language conformance workflow](diagrams/development/conformance-workflow.md)
- [Security review workflow](diagrams/development/security-review.md)
- [Release candidate validation](diagrams/development/release-validation.md)
- [Protocol change review](diagrams/development/protocol-change-review.md)
- [Test-vector generation](diagrams/development/test-vector-generation.md)
- [SDK compatibility testing](diagrams/development/sdk-compatibility.md)
- [Cryptographic implementation review](diagrams/development/cryptographic-implementation-review.md)
- [Vulnerability reporting and remediation](diagrams/development/vulnerability-response.md)
- [Module dependency boundaries](diagrams/development/dependency-boundaries.md)

## Existing architecture diagrams

- [Core workflow](../spec/workflows.md)
- [Architecture overview](../ARCHITECTURE.md)
- [Original diagram collection](diagrams/)
- [Protocol specification](../spec/protocol.md)

## Reader routes

**First-time users:** End-to-end user journey → Transaction to rating → Cross-platform portability → Disclosure comparison.

**Developers:** First-time integration → SDK initialization → Message flow → Verification decision tree → Conformance workflow.

**Protocol reviewers:** Credential validation → Multi-issuer reputation → Data visibility → Security review → Test-vector generation.
