# Security audit checklist

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define pre-release cryptographic and operational audit gates.

## Proposed design

Audit protocol specification, circuits, parameters, test vectors, fuzzing, side channels, dependencies, key custody, collusion and privacy claims.

## Conceptual diagram

```mermaid
flowchart TD
  S[Spec frozen] --> C[Cryptographic review]
  C --> I[Implementation audit]
  I --> T[Adversarial and cross-language tests]
  T --> R[Release decision]
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
