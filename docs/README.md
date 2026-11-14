# CipherRep documentation index

**All architecture and security designs are planning drafts until explicitly marked accepted.**

## Architecture and specification
- [System architecture](../ARCHITECTURE.md)
- [Cryptographic construction](../spec/cryptographic-design.md)
- [Trust and collusion model](../spec/trust-model.md)
- [Reputation arithmetic](../spec/reputation-mathematics.md)
- [Identity and Sybil resistance](../spec/identity-and-sybil-resistance.md)
- [Aggregate completeness and integrity](../spec/aggregation-integrity.md)
- [Canonical wire format](../spec/wire-format.md)
- [Cryptographic suite registry](../spec/cryptographic-suites.md)
- [Protocol state machines](../spec/protocol-state-machines.md)
- [Error taxonomy](../spec/error-codes.md)
- [Protocol versioning](../spec/versioning-and-compatibility.md)
- [Language-neutral API contract](../sdk/API_SPEC.md)
- [Attack scenarios](../security/attack-scenarios.md)
- [Privacy leakage matrix](../security/privacy-leakage-matrix.md)
- [Key management](../security/key-management.md)
- [Security invariants](../security/security-invariants.md)
- [Security audit checklist](../security/audit-checklist.md)
- [Integration guide](../docs/integration-guide.md)
- [Deployment models](../docs/deployment-models.md)
- [Reference use cases](../docs/reference-use-cases.md)
- [Implementation roadmap](../docs/implementation-roadmap.md)

## Workflow and architecture diagrams
- [Credential lifecycle](../docs/diagrams/credential-lifecycle.md)
- [Encrypted aggregation sequence](../docs/diagrams/encrypted-aggregation.md)
- [Zero-knowledge proof lifecycle](../docs/diagrams/zero-knowledge-proof.md)
- [Reputation snapshot state machine](../docs/diagrams/reputation-state-machine.md)
- [Threat and attack tree](../docs/diagrams/threat-attack-tree.md)
- [Key lifecycle](../docs/diagrams/key-lifecycle.md)
- [Deployment topology](../docs/diagrams/deployment-topology.md)
- [Cryptographic architecture](../docs/diagrams/cryptographic-architecture.md)
- [Language-neutral architecture](../docs/diagrams/language-neutral-architecture.md)
- [Privacy boundaries](../docs/diagrams/privacy-boundaries.md)
- [Cross-platform reputation](../docs/diagrams/cross-platform-reputation.md)

## Architecture decision records
- [Language-neutral protocol and Rust reference](adr/0001-language-neutral-protocol.md)
- [Homomorphic encryption selection](adr/0002-homomorphic-encryption.md)
- [Zero-knowledge proof system selection](adr/0003-zero-knowledge-proof-system.md)
- [Complete eligible rating set and negative events](adr/0004-reputation-completeness.md)
- [Unlinkability and Sybil-resistance model](adr/0005-identity-and-sybil-resistance.md)
- [Aggregation decentralization and custody](adr/0006-aggregation-deployment.md)

## Existing foundation
- [Protocol](../spec/protocol.md)
- [Original workflows](../spec/workflows.md)
- [Threat model](../spec/threat-model.md)
- [Conformance](../spec/conformance.md)
