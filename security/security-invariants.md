# Security invariants

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define properties that must hold for every accepted presentation.

## Proposed design

Examples: eligible authenticated contributions only; no duplicate authorization; complete snapshot; bounded arithmetic; audience-bound fresh proof; no unsupported suite acceptance.

## Conceptual diagram

```mermaid
flowchart TD
  E[Eligibility] --> A[Accept]
  U[Uniqueness] --> A
  C[Completeness] --> A
  P[Proof validity] --> A
  F[Freshness and context] --> A
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
