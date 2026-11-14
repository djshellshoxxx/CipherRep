# Identity and Sybil resistance

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Separate cryptographic unlinkability from economic authenticity and issuer admission policy.

## Proposed design

Define issuer trust tiers, one-rating-per-eligible-event nullifiers, pseudonym scopes, collusion response and privacy costs.

## Conceptual diagram

```mermaid
flowchart TD
  E[Completed eligible event] --> A[One-use authorization]
  A --> N[Scoped nullifier]
  N --> U{Previously used?}
  U -->|Yes| R[Reject]
  U -->|No| C[Accept eligible contribution]
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
