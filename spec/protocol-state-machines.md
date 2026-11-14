# Protocol state machines

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Define credential, contribution, snapshot and presentation states and transitions.

## Proposed design

Distinguish revoked, expired, superseded, rejected and disputed; transitions must be auditable and monotonic where applicable.

## Conceptual diagram

```mermaid
stateDiagram-v2
  [*] --> Authorized
  Authorized --> Issued
  Issued --> Validated
  Validated --> Included
  Issued --> Rejected
  Included --> Superseded
  Included --> Revoked
  Authorized --> Expired
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
