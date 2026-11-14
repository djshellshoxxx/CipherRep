# ADR-0009: Relationship-diversity weighting

**Status:** Accepted product direction; formula and cryptographic implementation pending.

CipherRep reputation confidence SHALL reward both distinct eligible counterparties (**breadth**) and repeat eligible transactions distributed across those counterparties (**depth**). One counterparty issuing many ratings MUST have diminishing marginal influence. A broad set of repeat counterparties SHOULD be stronger evidence than either a single prolific counterparty or many one-off counterparties, subject to a verifier-selected policy.

**Separate rating quality from evidence confidence.** A high average rating does not imply broad independent evidence. Negative ratings MUST remain in the complete eligible set. No legacy marketplace ratings may be imported (ADR-0007).

Unique counterparties MUST be established by a policy-defined identity/eligibility mechanism, not merely wallet addresses. Fraud rings can still fabricate many identities and repeated trades; weighting alone does not prevent collusion.

Candidate metrics: U=number of unique eligible counterparties; n_i=eligible rating count for counterparty i; T=sum(n_i); R_k=count of counterparties with n_i>=k; D=sum(min(n_i,cap)). An MVP may prove U>=u_min, R_2>=r_min, T>=t_min, alongside an independent quality threshold. A final composite formula and caps require adversarial testing, fixed-point arithmetic and proof-system benchmarking.

Acceptance criteria: enforce complete snapshot, uniqueness, bounded contributions, negative-rating inclusion, unlinkable presentations where feasible, cross-language test vectors, and explicit residual collusion risk. Related: [spec](../../spec/relationship-diversity-confidence.md).
