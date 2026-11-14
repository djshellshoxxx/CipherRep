# Integration guide

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Guide third-party applications through issuer setup, holder workflows and independent verification.

## Proposed design

Document illustrative pseudocode only until suite/API frozen. Require policy and trust roots pinned by verifiers.

## Conceptual diagram

```mermaid
flowchart TD
  A[Developer selects role] --> I[Configure issuer or verifier trust]
  I --> S[Choose supported suite]
  S --> W[Exchange canonical messages]
  W --> V[Verify locally]
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
