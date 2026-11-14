# Reputation arithmetic profile R0 (suite-independent)

**Status:** draft mathematical semantics; candidate for stable v1.

Ratings r_i are integers in [0,100], each included at most once under the applicable policy. For a committed eligible set with N ratings, S = sum(r_i). The verifier accepts a threshold T in [0,100] and minimum count M >= 1 only if:

```text
N >= M
100 * S >= T * N
0 <= S <= 100 * N
```

This avoids division, rounding ambiguity and floating-point inconsistencies. For a 90 threshold, S=1800,N=20 passes; S=1799,N=20 fails. N=0 always fails. N=1,M=20 fails even for r=100. A threshold of 100 requires every counted rating to be 100. The maximum allowed N and integer bit widths MUST be pinned by a later suite, and every implementation MUST reject overflow rather than wrap.

This profile specifies arithmetic only. It does not assert that the included set is complete, that contributions are genuine, or that encrypted arithmetic is correct; those require separate proofs and trust policies.
