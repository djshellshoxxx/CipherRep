# Deployment models

> **Status:** Planning draft; not a finalized normative specification or implemented feature.

## Purpose

Compare single-operator, threshold-operated, federated and decentralized approaches.

## Proposed design

List key custody, availability, collusion, auditability, costs and privacy tradeoffs for each. Do not imply full decentralization without a design.

## Conceptual diagram

```mermaid
flowchart TD
  P[CipherRep protocol] --> L[Local application]
  P --> H[Hosted aggregation]
  P --> F[Federated issuers]
  P --> T[Threshold-operated custodians]
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
