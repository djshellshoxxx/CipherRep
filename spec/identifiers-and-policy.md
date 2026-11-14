# Identifiers and policy semantics — draft

Define typed logical identifiers: protocol_version, suite_id, domain_id, issuer_id, policy_id, snapshot_id, epoch_id, authorization_id and audience_id. Treat each as an opaque byte sequence with a type tag, not a human-readable string with implicit case normalization. Exact byte lengths and wire representation remain undecided.

A verifier MUST select its own accepted issuer trust roots, domain, minimum count, threshold, allowed suite IDs, maximum snapshot age, and replay/audience policy. The presentation MUST bind to those selected values. Applications MUST NOT treat a user-supplied policy identifier as proof that the policy is trusted.

For replay resistance, a verifier challenge SHOULD be unpredictable and scoped to an audience, purpose and expiry. The precise challenge length, entropy requirement and transcript encoding will be pinned by the selected suite.

Domains MUST be separate: reputation for a marketplace trade cannot silently count as lending reputation. Cross-domain composition requires an explicitly versioned policy.
