# ADR-0007: CipherRep-native ratings only

- **Status:** Accepted product policy (2026-11-14)
- **Scope:** Reputation eligibility and cross-platform portability

## Decision

CipherRep MUST NOT import, translate, scrape, or count pre-existing reputation scores or ratings from external marketplaces or third-party rating systems. Ratings become eligible only when issued as **native CipherRep credentials** for an eligible event under a CipherRep-compatible authorization policy.

A third-party application MAY implement CipherRep and issue native CipherRep credentials for its own newly eligible events. A verifier MAY accept credentials from multiple such issuers under an explicit trust and domain policy. **Portability of CipherRep-native reputation is allowed; conversion of external reputation into CipherRep reputation is not.**

Existing marketplace ratings, review counts, seller scores, historical reputation exports, and third-party API scores MUST NOT be silently mapped into CipherRep ratings, even when signed by an importer.

## Rationale

Avoid unverifiable historical eligibility, inconsistent rating semantics, unverifiable negative-rating completeness, and reputation laundering through external score imports. Maintain a uniform native issuance lifecycle.

## Consequences

- No legacy reputation import or migration adapter.
- New users begin without CipherRep-native ratings.
- A marketplace integration issues native ratings for new eligible events, rather than importing its old review database.
- Cross-platform aggregation remains conditional on issuer trust, canonical completeness, and domain policy.
- This is a product rule, not a cryptographic guarantee: issuer eligibility and Sybil resistance remain unresolved engineering problems.

## Conformance

Reject credentials labeled as imported, converted, or legacy-derived reputation. Tests MUST distinguish a native credential issued by a participating marketplace from an external score wrapped in a CipherRep envelope.
