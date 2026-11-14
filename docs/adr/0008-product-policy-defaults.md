# ADR-0008: CipherRep product and privacy defaults

- **Status:** Accepted policy direction (2026-11-14); cryptographic implementation details remain open
- **Supersedes:** no prior accepted cryptographic ADRs

## Decisions

1. **Issuance:** Credential issuance is permissionless at the protocol level. Each verifier independently decides which issuers and policies to trust.
2. **Bidirectional ratings:** Each eligible transaction MAY authorize each participant to rate the other, with distinct one-use authorizations.
3. **Complete scope:** An accepted reputation claim MUST include every eligible rating in its declared domain, policy, issuer scope, and epoch. No selective removal of unfavorable ratings. How this is proven remains an open blocker.
4. **No legacy imports:** Only CipherRep-native ratings count. See ADR-0007.
5. **Private counts:** Exact count SHOULD remain hidden; a proof of minimum count is the default. Some suites may expose count and MUST declare this leakage.
6. **Private issuers:** Do not reveal the issuer list by default; a verifier's trust policy may require disclosures or proof of membership in a trusted issuer set.
7. **Unlinkability:** Presentations SHOULD be unlinkable across relying parties and bound to a specific verifier audience, purpose, nonce, and expiration. Precise achievable guarantees await cryptographic design.
8. **Proof thresholds:** Support multiple thresholds with standardized policy tiers to reduce extraction through repeated queries.
9. **Pseudonyms:** Support domain-separated reputation identities without mandatory universal public identifiers.
10. **Recovery:** Recovery is optional and MUST NOT require universal central custody.
11. **Offline verification:** Supported when verifier already possesses sufficiently fresh authenticated trust, revocation and snapshot material.
12. **No required server or blockchain:** Local verification is a core goal; hosted infrastructure and on-chain adapters are optional.
13. **Multiple profiles:** A shared logical API may support different cryptographic suites; differing guarantees MUST be explicitly distinguished.
14. **Open interoperability:** The language-neutral specification and independent conformance tests are authoritative, not any one SDK.
15. **Rating weights:** Uniform integer rating weights for initial profile; transaction-value weighting and age decay are deferred to separate future profiles.
16. **Disputes:** Support auditable correction, revocation and superseding snapshots rather than deleting historical entries.
17. **Issuer continuity and abuse:** Anti-Sybil admission, identity reset and wash-trading defenses remain configurable policy research, not solved cryptographically.

## Non-decisions

This ADR does NOT select Paillier, proof backend, credential scheme, snapshot governance, custodians, wire encoding or key recovery mechanics. These remain subject to separate ADRs and empirical validation.

## Verification gates

A v1 profile cannot claim complete, unlinkable, private reputation until tests and independent review demonstrate the relevant security properties under its published trust model.
