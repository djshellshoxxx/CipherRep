# Verifier outcomes and fail-closed behavior — draft

A verifier returns exactly one primary status:

- **VALID:** cryptographic verification, trusted policy, authenticated snapshot, freshness and replay-context checks all pass.
- **INVALID:** a well-supported protocol instance violates a check.
- **UNSUPPORTED:** required version, suite, critical extension or policy feature is unknown.
- **STALE:** proof or required trust/snapshot material is outside accepted freshness bounds.
- **INDETERMINATE:** required trusted information is unavailable, not proven false.

Suggested reason codes: INVALID_ENCODING, INVALID_SIGNATURE, INVALID_PROOF, INVALID_ELIGIBILITY, DUPLICATE_AUTHORIZATION, AGGREGATE_MISMATCH, INCOMPLETE_SNAPSHOT, POLICY_MISMATCH, AUDIENCE_MISMATCH, EXPIRED_PRESENTATION, REVOKED_CREDENTIAL, UNSUPPORTED_VERSION, UNSUPPORTED_SUITE, STALE_SNAPSHOT, TRUST_DATA_UNAVAILABLE.

Only VALID authorizes a positive reputation claim. UNSUPPORTED, STALE and INDETERMINATE MUST NOT be coerced to true. Reason codes must not reveal private witness information; exact public error detail policy is a future decision.
