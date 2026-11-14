# Relationship-diversity confidence specification

**Status:** Policy direction accepted; exact weighting algorithm, identity model, proof circuit and parameters undecided.

## Goal

Confidence should increase with the breadth of unique eligible counterparties and with repeated interactions distributed among those counterparties, with diminishing returns for concentration. Rating quality and evidence confidence are distinct claims.

## Model

For one domain, epoch and complete eligible snapshot, let n_i be the count of native CipherRep ratings from unique eligible counterparty i. Let U be distinct counterparties and T=sum_i n_i.

Candidate policy metrics (not finalized): breadth U; repeat coverage R_k = number of counterparties with n_i>=k; saturated depth D=sum_i min(n_i,cap). A verifier may request proofs of U>=u_min, R_2>=r_min and T>=t_min. Exact counts and relationship graph should remain private by default.

## Reference patterns

- 1 counterparty × 100 ratings: U=1, R_2=1 (concentrated).
- 100 counterparties × 1 rating: U=100, R_2=0 (broad but shallow).
- 20 counterparties × 5 ratings: U=20, R_2=20 (broad and repeated).

These examples are **not calibrated fraud probabilities**. A colluding ring may mimic the third pattern.

## Requirements

1. Only native CipherRep eligible ratings count; no imported reputation.
2. Complete eligible set MUST include unfavorable ratings.
3. Scoped unique-counterparty identity and repeated-event authenticity MUST be provable under declared trust assumptions.
4. No single counterparty may contribute unlimited confidence.
5. Proof MUST bind policy, issuer trust, domain, snapshot, audience and freshness.
6. The protocol MUST not claim non-collusion from diversity arithmetic alone.
7. Test negative ratings, duplicate authorization, Sybil rings, one-off raters, concentrated repeats, and balanced repeats.

**Open:** anti-Sybil identity continuity, proof-friendly integer formula, per-issuer weighting, epoch handling and privacy leakage.
