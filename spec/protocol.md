# CipherRep Protocol — Language-Neutral Specification

**Status:** Draft 0.1 (non-normative, pre-implementation). **Target:** eventual CipherRep v1.0. This document defines a proposed interoperability contract; it does not claim that a secure end-to-end construction has been selected.

## 1. Scope and goals

CipherRep enables a holder to demonstrate that an aggregate reputation score from authenticated, eligible ratings satisfies a verifier's policy without disclosing individual ratings, transaction history, or the exact aggregate. The protocol MUST remain implementable in any programming language, without a mandatory blockchain, service operator, or SDK.

Non-goals: proof of real-world identity, automatic Sybil resistance, proof that a transaction was satisfactory, anonymity against global traffic analysis, and trustless rating truthfulness.

## 2. Roles

- **Holder:** controls presentation and proves claims.
- **Rater:** issues a rating credential for an authorized event.
- **Eligibility issuer:** authorizes a rating slot based on a completed transaction; may be the marketplace.
- **Aggregator:** validates contributions and computes encrypted aggregates.
- **Key custodians:** optionally perform threshold decryption or jointly authorize aggregate attestations.
- **Verifier:** checks cryptographic proof, issuer trust, policy, snapshot freshness and replay context.
- **Registry:** optional source of issuer keys, revocation data, suites, and policies; MUST be replaceable by pinned local trust configuration.

One actor may play multiple roles; implementations MUST document resulting trust changes.

## 3. High-level lifecycle

1. Establish a transaction-completion/eligibility attestation and a one-use rating authorization.
2. Produce a signed rating credential and commitment; encrypt the rating for the aggregation scheme.
3. Validate signature, eligibility, allowed rating range, revocation and unique authorization nullifier; append an authenticated contribution to a committed snapshot.
4. Aggregate ciphertexts and counts under a fixed suite, domain and epoch; bind results to the committed set.
5. Produce a zero-knowledge proof of the policy predicate and the required links between eligible credentials, commitments and the aggregate.
6. Verify the proof using public parameters, snapshot commitment, policy, issuer trust configuration, context and expiration.

A bare proof that a private number is at least a threshold is **insufficient**: it MUST bind to authenticated eligible contributions and a committed, policy-defined selection of them.

## 4. Reputation model (initial profile)

Ratings are integers in [0, 100]. Each eligible rating contributes one point count and its value to the sum. For a fixed domain, epoch and eligibility policy, let S be the sum and N be the count. A policy claim for threshold T (integer [0, 100]) and minimum count M is:

```text
N >= M AND N > 0 AND 100 * S >= T * N
```

No floating-point operations are used in consensus/proof arithmetic. Circuit and verifier MUST enforce bounded N and S, integer overflow protection, credential eligibility, uniqueness, and the same canonical ordering/selection rule. Weighting, decay, multi-domain composition and negative events are future extensions requiring distinct policy IDs.

**Completeness challenge:** an individual holder can otherwise omit low ratings. v1 MUST specify whether a canonical, issuer-controlled append-only snapshot or another verifiable completeness mechanism defines the full rating set. Until this is resolved, claims MUST NOT be described as complete reputation.

## 5. Logical messages (not yet wire-stable)

The following objects are abstract schemas, not finalized JSON serialization:

| Object | Required logical fields |
|---|---|
| EligibilityAuthorization | protocol_version, suite_id, issuer_id, rating_domain, authorization_commitment, validity_window, policy_id, issuer_signature |
| RatingCredential | protocol_version, suite_id, rating_commitment, authorization_reference, rating_domain, issuer_id, signature, validity_window |
| EncryptedContribution | suite_id, ciphertext, commitment, authorization_nullifier, eligibility_proof, domain, epoch |
| AggregateSnapshot | suite_id, domain, epoch, policy_id, commitment_root, encrypted_sum, encrypted_count_or_public_count, selection_rule_id, signer_or_proof |
| ReputationPresentation | protocol_version, suite_id, proof_type, public_inputs, proof_bytes, policy_id, snapshot_id, verifier_context, expiry |
| VerificationPolicy | accepted_suite_ids, accepted_issuers, domain, threshold, minimum_count, maximum_snapshot_age, revocation_policy, context |

No exact field byte encodings, algorithms, key sizes, or signature suites are standardized in this draft. Implementations MUST NOT claim cross-language interoperability until those parameters and test vectors are published.

## 6. Proposed wire contract

- Define canonical CBOR as the preferred binary format **subject to a finalized deterministic encoding profile**; diagnostic JSON is for developer tooling only.
- Define exact field-number registry, integer types, byte-string limits, Unicode policy, mandatory/optional fields, and rejection of unknown critical fields before v1.
- Domain-separate all signatures, commitments, hashes, nullifiers and Fiat–Shamir transcripts using protocol version, suite ID, message type and application domain.
- Hash canonical encoded bytes; never hash a non-canonical JSON rendering.
- Public verification inputs MUST bind threshold, minimum count, policy ID, issuer-trust root, epoch/snapshot root, verifier audience/challenge, expiration and proof suite.
- Verifiers MUST fail closed for unsupported versions, suites, parameters, expired or revoked attestations, malformed encodings, inconsistent roots and context mismatch.
- Unrecognized non-critical extensions may be ignored only if they are explicitly excluded from security-relevant transcript commitments.

## 7. Cryptographic suite selection — open design decision

The initial candidate uses additive homomorphic encryption (for example threshold Paillier), commitments, authenticated eligibility and a zero-knowledge proof. **Homomorphic aggregation does not automatically prove aggregate correctness.** A complete suite MUST specify:

- encryption scheme, key generation, ciphertext validity, bounds and threshold custody;
- rating commitments and proofs linking committed plaintexts to encrypted contributions;
- credential signature scheme and proof of authorized issuance;
- append-only inclusion and set-completeness mechanism;
- proof system and circuit for validity, uniqueness, aggregate integrity and threshold;
- public parameters, trusted setup (if any), verification key distribution and rotation;
- precise public leakage (count, domain, issuer set, epoch and proof metadata);
- revocation, freshness, replay protection and key compromise recovery.

A commitment-based ZK aggregation profile may be easier to implement, but MUST NOT be labeled homomorphic encryption unless it genuinely provides encrypted computation. Profile identifiers MUST distinguish different privacy/trust properties.

## 8. Verifier algorithm (abstract)

1. Parse strict canonical envelope; check supported version and suite.
2. Validate audience-bound challenge, expiry, domain and policy identifiers.
3. Resolve pinned or authenticated issuer trust material and revocation status.
4. Authenticate snapshot commitment, selection rule, epoch and freshness.
5. Verify ZK proof against all policy public inputs and authenticated aggregate binding.
6. Return an explicit result: valid / invalid / unsupported / stale / indeterminate; never treat unsupported as valid.

Offline verification is possible only when all necessary trust and revocation inputs are locally available and sufficiently fresh under policy.

## 9. Privacy and abuse controls

Presentations SHOULD be unlinkable across verifier contexts. Nullifiers MUST be scoped narrowly enough to prevent duplicate ratings without becoming universal tracking identifiers. Standardize threshold tiers to reduce score extraction by repeated queries. Metadata and timing correlation remain possible. Proof privacy does not prevent collusion, false ratings, wash trading or Sybil attacks; these require external issuer policy and economic defenses.

## 10. Interoperability requirements

Independent implementations MUST agree on canonical bytes, domain separation, public-input ordering, numeric bounds, rejection behavior, signatures, commitments, ciphertext semantics, proof verification, and policy evaluation. Publish positive and negative golden vectors with stable version IDs. No implementation may silently reinterpret a v1 message using different rules.

## 11. Versioning

Protocol major versions change incompatible semantics. Suites and policies have independently versioned IDs. The final v1 release MUST pin all algorithms, encodings and proof statements; this draft intentionally does not.

## 12. Open questions blocking v1

1. Who commits the complete eligible rating set, and how is selective omission prevented?
2. Can the ZK proof verify encrypted aggregation efficiently without trusting a decryption service?
3. Is rating count public, committed, or hidden?
4. How are negative ratings, disputes and revocations reflected in snapshots?
5. What issuer trust and Sybil-resistance model applies across platforms?
6. Which cryptographic suite, proof backend, canonical encoding and key lifecycle are auditable and practical?
7. How can users avoid linkability when proving portable reputation across independent issuers?

See [threat model](threat-model.md), [workflows](workflows.md), and [conformance](conformance.md).
