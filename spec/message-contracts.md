# Language-neutral logical message contracts — draft

These are logical records, not a frozen wire format. Unknown security-critical fields must fail closed.

| Record | Required logical members |
|---|---|
| Authorization | version, suite, domain, issuer, event_commitment, one_use_scope, policy, validity, signature |
| RatingCredential | version, suite, authorization_reference, rating_commitment, issuer, signature, validity |
| EncryptedContribution | version, suite, domain, epoch, ciphertext, rating_commitment, scoped_nullifier, validity_evidence |
| AggregateSnapshot | version, suite, domain, epoch, policy, eligible_set_root, aggregate_ciphertext, count_representation, completeness_evidence |
| PresentationRequest | version, accepted_suites, audience, challenge, policy, expiration |
| ReputationPresentation | version, suite, snapshot_reference, policy, public_inputs, proof, audience, challenge, expiration |
| VerificationResult | status, reason_code, accepted_policy, snapshot_reference |

Each implementation MUST reject missing required fields, duplicate fields, invalid numeric ranges, unsupported versions and suites, unknown critical extensions, and inconsistent references. Canonical encoding, field numbering, hashes, signature algorithms and exact byte constraints are deferred to D3/D4.

No network transport is mandatory. These objects may be exchanged by local files, P2P transport, HTTP or other means without changing verification semantics.
