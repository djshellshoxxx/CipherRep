# Normative terminology and roles — draft

This document fixes language-independent concepts, not cryptographic choices.

- **Eligible event:** a completed event satisfying an issuer's published authorization policy.
- **Authorization:** an issuer assertion that exactly one rating opportunity exists for an eligible event and domain.
- **Rating:** bounded integer contribution in [0,100].
- **Credential:** authenticated statement binding a rating commitment to authorization and policy.
- **Contribution:** encrypted rating, commitment and eligibility evidence submitted for inclusion.
- **Canonical eligible set:** the complete, policy-defined set of valid contributions for a domain and snapshot epoch. The mechanism enforcing completeness remains undecided.
- **Snapshot:** authenticated commitment to a canonical eligible set, its epoch and policy.
- **Aggregate:** sum and count over the canonical eligible set, with verifiable binding to the snapshot.
- **Holder:** party seeking to prove a reputation claim.
- **Rater:** party producing an authorized rating.
- **Issuer:** party attesting event eligibility and/or credential authenticity.
- **Verifier:** party validating a presentation under its independently selected trust policy.
- **Presentation:** audience-bound proof and authenticated public inputs asserting a reputation predicate.
- **Suite:** pinned algorithms, parameters, encodings and verification semantics.
- **Policy:** versioned constraints on issuer trust, domain, threshold, count, snapshot freshness and revocation.

The terms MUST NOT be conflated: encryption is not authenticity; a proof of a threshold is not a proof of completeness; pseudonymity is not Sybil resistance.
