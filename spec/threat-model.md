# Threat Model (Draft)

## Assets and desired properties

- Confidentiality of individual ratings and transaction links.
- Integrity, authenticity and completeness of eligible rating sets.
- Correct threshold claims with a nonzero, policy-specified minimum sample.
- Cross-verifier unlinkability, replay resistance, freshness and independent verification.
- Recovery from compromised issuers, custodians, and cryptographic parameters.

## Adversaries

Dishonest holder; malicious rater; Sybil ring; compromised issuer; aggregator that omits low scores or fabricates entries; colluding key custodians; malicious verifier probing multiple thresholds; observer correlating network metadata; attacker replaying proofs; compromised signing keys.

## Main attack paths and intended mitigations

| Attack | Proposed mitigation |
|---|---|
| Fake ratings | Signed eligibility authorizations bound to verified events |
| Duplicate ratings | Domain/epoch-scoped one-use nullifiers |
| Selective omission | Canonical authenticated full-set snapshot and auditable inclusion/completeness |
| Malformed ciphertext / out-of-range rating | Zero-knowledge validity and plaintext-ciphertext consistency proofs |
| Fabricated aggregate | Verifiable linkage between ciphertext set, aggregate, and proof |
| False score due to arithmetic overflow | Fixed-width bounds and exact integer constraints |
| Stale positive reputation | Expiring snapshots, revocation policy, recent epoch requirements |
| Threshold probing | Coarse standardized tiers, audience binding and policy constraints |
| Cross-site tracking | Unlinkable presentations and domain separation |
| Colluding custodians | Explicit threshold assumption, audits and key rotation |
| Malicious verifier or registry | Pinned trust roots, authenticated policy and strict validation |
| Wash trading / Sybil attacks | External issuer eligibility and anti-abuse controls; not solved cryptographically |

## Trust assumptions

The draft does not yet define a fully trustless design. Rating truthfulness depends on issuer and marketplace policies. Completeness depends on authenticated snapshot governance. Threshold encryption depends on key-custodian honesty assumptions. ZK soundness depends on circuit correctness and cryptographic setup. Deployment metadata may defeat cryptographic unlinkability.

## Required security review before release

Specify algorithms and parameter sizes; audit cryptographic suite and circuits; publish attack tests and independent cross-language vectors; review setup and key lifecycle; assess coercion, collusion, DoS and side-channel behavior; document residual privacy leakage and operator trust.
