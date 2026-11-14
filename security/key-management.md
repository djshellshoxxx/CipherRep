# Key management

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define signing, encryption, threshold-share, proof parameter and verification key lifecycle.

## Proposed design

Document generation, rotation, revocation, backup, share resharing, compromise recovery and zeroization requirements.

## Conceptual diagram

```mermaid
flowchart TD
  G[Generate] --> D[Distribute public keys and shares]
  D --> U[Use]
  U --> R[Rotate]
  R --> U
  U --> C[Compromise detected]
  C --> X[Revoke and recover]
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
