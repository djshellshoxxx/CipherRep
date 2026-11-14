# CipherRep — Reader-Friendly Workflow Diagrams

These diagrams describe the **intended protocol**, not deployed functionality. They deliberately show the roles separately, even when one application operates multiple roles.

## 1. First-time viewer: what happens?

```mermaid
flowchart TD
  A[Two people complete a transaction] --> B[Platform authorizes one rating]
  B --> C[Counterparty issues authenticated rating]
  C --> D[Encrypted rating joins committed reputation set]
  D --> E[Service aggregates without reading individual scores]
  E --> F[Holder requests proof of score threshold]
  F --> G[Another app checks proof and trusted policy]
  G --> H{Valid and fresh?}
  H -->|Yes| I[Grant reputation-based access]
  H -->|No| J[Do not accept claim]
```

## 2. Customer / reputation holder journey

```mermaid
flowchart TD
  A[Finish a trade] --> B[Receive eligible rating credential]
  B --> C[Credential enters reputation snapshot]
  C --> D[Choose app requesting a reputation threshold]
  D --> E[Review claim and audience]
  E --> F[Generate audience-bound ZK presentation]
  F --> G[Submit proof, not history]
  G --> H[App verifies claim]
```

The holder does not automatically control which eligible ratings count; snapshot completeness must be independently enforceable.

## 3. Rater and issuing marketplace journey

```mermaid
flowchart TD
  A[Marketplace records eligible completed trade] --> B[Issue one-time rating authorization]
  B --> C[Rater chooses score]
  C --> D[Sign rating credential and encrypt contribution]
  D --> E[Validate rating bounds and authorization]
  E --> F{Duplicate or revoked?}
  F -->|Yes| G[Reject contribution]
  F -->|No| H[Commit eligible contribution]
```

## 4. Aggregator and key custodians

```mermaid
flowchart TD
  A[Read committed eligible contributions] --> B[Verify inclusion, uniqueness and policy]
  B --> C[Homomorphically combine ciphertexts]
  C --> D[Commit aggregate and snapshot metadata]
  D --> E[Produce cryptographic binding evidence]
  E --> F[Authorized proof or threshold decryption workflow]
  F --> G[Publish authenticated snapshot inputs]
```

**Trust boundary:** encrypted arithmetic alone cannot certify which ratings were included. A cryptographic link to the authenticated snapshot and a verifiable completeness policy are required. Custodians must not be assumed incapable of colluding.

## 5. Independent verifier journey

```mermaid
flowchart TD
  A[Receive presentation] --> B[Parse canonical envelope]
  B --> C[Check suite, audience, nonce, expiration]
  C --> D[Check issuer policy and snapshot freshness]
  D --> E[Verify aggregate integrity and ZK proof]
  E --> F{All checks pass?}
  F -->|Yes| G[Accept threshold claim only]
  F -->|No| H[Reject or return indeterminate]
```

## 6. Sequence: separation of responsibilities

```mermaid
sequenceDiagram
  participant R as Rater
  participant I as Issuer / Marketplace
  participant A as Aggregator
  participant H as Holder
  participant V as Verifier
  I->>R: One-use rating authorization
  R->>A: Signed credential + encrypted contribution
  A->>A: Validate and commit eligible set
  A-->>H: Authenticated aggregate snapshot / proof inputs
  V->>H: Threshold policy + audience challenge
  H->>H: Generate policy-bound proof
  H->>V: ZK presentation
  V->>V: Verify proof, issuer trust, snapshot, freshness
  V-->>H: Accept or reject claim
```

## 7. What the verifier learns

| Intended disclosure | Hidden unless policy explicitly reveals it |
|---|---|
| Threshold met, minimum count met | Exact score and individual ratings |
| Domain and policy ID | Individual transaction history |
| Snapshot epoch and cryptographic suite | Counterparties and rating content |
| Trusted issuer policy / root | Holder's unrelated platform identities |

This privacy goal depends on the chosen cryptographic suite and deployment metadata. A proof alone cannot conceal IP addresses, network timing, or a globally identifying issuer policy.
