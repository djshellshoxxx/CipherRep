# Trust and collusion model

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Specify issuer, aggregator, custodian, holder and verifier trust assumptions.

## Proposed design

Evaluate collusion scenarios and specify minimum honest parties; do not assume a threshold key prevents colluding custodians from decrypting.

## Conceptual diagram

```mermaid
flowchart LR
  I[Issuer trust] --> Q[Eligible rating set]
  A[Aggregator integrity] --> Q
  K[Key custodian threshold] --> D[Privacy assumption]
  Q --> V[Verifier confidence]
  D --> V
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
