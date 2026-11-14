# Language-neutral conformance fixture contract — draft

Each fixture SHOULD be represented in a deterministic machine-readable format with these logical members:

```json
{
  "fixture_version": "0.1",
  "fixture_id": "arithmetic-threshold-equality",
  "profile": "R0-arithmetic",
  "input": {"ratings": [90, 90], "threshold": 90, "minimum_count": 2},
  "expected": {"status": "VALID"},
  "notes": "Arithmetic-only fixture; not a cryptographic proof"
}
```

Required suites: arithmetic boundaries; malformed messages; unknown versions; unknown critical fields; invalid transitions; policy mismatches; replay and expiry; revoked credentials; incomplete sets; altered ciphertexts; proof binding; cross-language canonical bytes once D4 is decided.

Fixture files MUST clearly distinguish arithmetic/mock fixtures from cryptographic conformance. A reference verifier MUST NOT accept mock fixtures as actual proofs.
