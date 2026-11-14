# CipherRep Conformance Plan (Draft)

This is a plan, not a certification or passing test suite.

## Conformance profiles

- **Core verifier:** strict envelope decoding, policy validation, snapshot authentication, proof verification.
- **Issuer:** authorization, credential signing, revocation and duplicate prevention.
- **Aggregator:** contribution validity, encrypted arithmetic, committed set and completeness proof.
- **Holder:** audience-bound presentation and privacy-preserving witness handling.
- **Transport adapter:** moves canonical messages without modifying cryptographic meaning.

## Required test vectors before v1

1. Canonical serialization round-trip and byte-for-byte equivalence across Rust, TypeScript, Python and Go.
2. Valid signature, wrong issuer, wrong domain, wrong policy, wrong suite, altered signed field.
3. Invalid rating ranges, zero count, insufficient count, threshold equality, off-by-one threshold, maximum safe aggregate and overflow.
4. Repeated authorization/nullifier, revoked credential, stale epoch and incomplete snapshot.
5. Valid ciphertext aggregation, invalid ciphertext, altered aggregate and plaintext-commitment mismatch.
6. Proof bound to correct public inputs; fail for changed threshold, issuer root, audience, nonce, expiry, snapshot or circuit version.
7. Negative parser cases: duplicate keys, unknown critical fields, malformed bytes, oversized payloads and non-canonical encoding.
8. Privacy tests for presentation correlation and repeated threshold probing under the declared leakage model.

Each vector MUST include: version, suite, canonical input bytes, expected output or error category, and rationale. Independent implementations MUST produce identical verification outcomes.

## Compatibility gates

No claim of v1 conformance until: complete normative spec, pinned cryptographic suite, published test vectors, independent implementation verification, negative-case coverage, and security review. Do not publish a security badge based on documentation-only tests.
