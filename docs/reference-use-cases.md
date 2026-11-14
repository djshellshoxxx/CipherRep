# Reference use cases

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Describe portable reputation for marketplaces, escrow, P2P trading, lending and freelancing.

## Proposed design

Define issuer eligibility and verifier policy per domain; do not combine unrelated domains without an explicit composition policy.

## Conceptual diagram

```mermaid
flowchart TD
  A[Marketplace A] --> C[CipherRep credential ecosystem]
  B[Marketplace B] --> C
  C --> H[Holder private reputation proof]
  H --> E[Escrow platform]
  H --> F[Freelancing platform]
  H --> P[P2P marketplace]
```

## Decisions required

- Define the exact trust assumptions and verifier-visible inputs.
- Select canonical serialization, algorithms and parameters where applicable.
- Define failure cases, privacy leakage, and independent test vectors.
- Record the accepted design in an ADR before treating this as normative.

## Acceptance criteria

- Reviewable specification with explicit MUST/SHOULD requirements once finalized.
- Positive and negative cross-language conformance fixtures.
- Documented threat-model implications and versioning.

See [protocol draft](../spec/protocol.md) and [threat model](../spec/threat-model.md) where applicable.
