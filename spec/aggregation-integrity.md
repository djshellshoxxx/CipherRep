# Aggregate completeness and integrity

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Specify verifiable membership, uniqueness and completeness of all eligible contributions.

## Proposed design

Critical blocker: decide who defines canonical full set; prevent holders/aggregators omitting unfavorable ratings. Define authenticated snapshots and soundness statements.

## Conceptual diagram

```mermaid
flowchart TD
  E[Eligible events] --> L[Canonical committed ledger]
  L --> C[Commitment root]
  L --> A[All eligible ciphertexts]
  A --> H[Homomorphic aggregate]
  C --> P[Completeness and integrity proof]
  H --> P
  P --> V[Verifier]
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
