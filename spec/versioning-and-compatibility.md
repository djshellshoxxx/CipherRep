# Protocol versioning

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define semantic compatibility, suite lifecycle and extension handling.

## Proposed design

Major version changes cryptographic meaning; minor version only compatible noncritical additions; test vectors pinned to version and suite.

## Conceptual diagram

```mermaid
flowchart TD
  M[Incoming version] --> S{Major supported?}
  S -->|No| R[Reject]
  S -->|Yes| C{Critical fields known?}
  C -->|No| R
  C -->|Yes| V[Validate suite and policy]
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
