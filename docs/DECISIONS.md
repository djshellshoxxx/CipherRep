# Accepted CipherRep policy decisions

**As of 2026-11-14.** These are product/protocol requirements, not claims of completed cryptographic implementation.

- [ADR-0007: Native ratings only](adr/0007-native-ratings-only.md): no importing or converting external marketplace reputation.
- [ADR-0008: Product and privacy defaults](adr/0008-product-policy-defaults.md): permissionless issuance, verifier-selected trust, bidirectional ratings, complete eligible scope, private counts, unlinkable audience-bound proofs, offline verification, optional infrastructure, versioned profiles, corrections and deferrals.
- [Native issuance policy](../spec/native-issuance-policy.md): precise distinction between integrating a marketplace with native issuance and importing existing ratings.

## Still undecided

- Cryptographic construction and parameters
- Snapshot completeness mechanism and governance
- Encryption key custody and collusion tolerance
- Unlinkable identity continuity and Sybil defenses
- Canonical wire encoding and exact proof statements
- Recovery and dispute protocol mechanics

See [decision register](decision-register.md) and [implementation plan](../PLAN.md).
