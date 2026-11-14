# Native rating issuance and eligibility — product policy

**Status:** Policy accepted; normative cryptographic encoding pending.

## Eligibility rule

A reputation contribution is eligible only when:
1. An issuer operating under a CipherRep-compatible issuance policy authorizes a newly eligible event.
2. A rater produces a native CipherRep rating credential bound to that authorization.
3. The contribution passes signature, bounds, uniqueness, revocation, and domain-policy checks.
4. The contribution is included in the complete authenticated eligible set for the applicable snapshot.

External marketplace stars, review scores, ratings APIs, historical account reputation, imported CSV ratings, and translated legacy reputation credentials MUST NOT count toward CipherRep aggregates.

## Distinction: integration vs import

- **Allowed:** Marketplace A integrates CipherRep and issues native CipherRep credentials for newly completed eligible trades; those credentials can be considered by Marketplace B's verifier under B's issuer policy.
- **Not allowed:** Marketplace A uploads old seller scores and converts them to CipherRep credentials, even if the import process signs them.
- **Allowed:** Different native CipherRep issuers participate in a cross-platform reputation domain under an explicit verifier policy.
- **Not allowed:** Implicitly mixing unrelated domains or counting external ratings from a platform that has not implemented native issuance.

## Bidirectional issuance

An eligible event may create two separate one-use rating authorizations, one for each direction. Both are subject to uniqueness and revocation rules. No rating can be retroactively generated from an old external review solely to boost reputation.

## Required tests

- Accept a valid native credential under a trusted issuer policy.
- Reject a converted legacy review, imported score, and wrapped external rating.
- Reject reused authorization and unauthorized event.
- Reject out-of-range values, expired authorization and revoked contribution.
- Reject incomplete eligible set claims even when the remaining ratings are valid.

## Outstanding design issues

The cryptographic proof of native provenance, canonical eligible-set completeness, issuer admission policy, and unlinkable cross-platform composition remain to be specified and audited.
