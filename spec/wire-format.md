# Canonical wire format

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define byte-exact interoperable message encoding, field registry, and validation.

## Proposed design

Candidate deterministic CBOR; unresolved field numbers, byte limits, critical extension handling, normalization and hash domain separation.

## Conceptual diagram

```mermaid
flowchart LR
  O[Logical object] --> E[Canonical encoder]
  E --> B[Identical bytes]
  B --> H[Hash and signature]
  B --> D[Strict decoder]
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
