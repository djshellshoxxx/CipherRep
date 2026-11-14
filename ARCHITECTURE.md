# System architecture

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define roles, components, deployment boundaries, and implementation independence.

## Proposed design

A verifier consumes canonical proof envelopes and authenticated policy/snapshot inputs without requiring the issuer's SDK.

## Conceptual diagram

```mermaid
flowchart TD
  I[Eligibility issuer] --> R[Rater]
  R --> A[Contribution validator]
  A --> S[Authenticated snapshot]
  A --> H[Encrypted aggregator]
  H --> P[Proof workflow]
  S --> P
  P --> V[Independent verifier]
  T[Trust configuration] --> V
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
