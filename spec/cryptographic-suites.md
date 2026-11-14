# Cryptographic suite registry

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Pin algorithms, parameters, verification keys, proof system and rotation behavior per suite.

## Proposed design

Reject unknown suite IDs; no implicit negotiation downgrades; record test vectors and key lifecycle.

## Conceptual diagram

```mermaid
flowchart TD
  M[Envelope suite ID] --> S{Supported and permitted?}
  S -->|No| R[Reject]
  S -->|Yes| P[Load pinned parameters]
  P --> V[Verify]
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
