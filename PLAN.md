# CipherRep implementation plan

**Status:** executable planning baseline, 2026-11-14. This is not a production readiness claim.

## Objective

Deliver a language-neutral, independently verifiable reputation protocol in which authenticated encrypted ratings contribute to a canonical reputation snapshot and a holder can prove a policy threshold without revealing individual scores. Keep a Rust reference implementation and optional SDKs, but define wire compatibility through the normative specification and conformance vectors.

## Work that can start immediately (no cryptographic suite decision)

| ID | Deliverable | Acceptance criteria | Dependencies |
|---|---|---|---|
| P01 | Normative terminology and role glossary | Each role, message, and trust boundary has an unambiguous definition | None |
| P02 | Domain and policy identifier specification | Namespaced identifiers, collision rules, stable comparison, explicit rejection | None |
| P03 | Rating arithmetic specification | Integer-only score, count, threshold, overflow and boundary examples | None |
| P04 | Verifier result/error taxonomy | Fail-closed outcomes, consistent error categories, no ambiguous boolean for indeterminate | None |
| P05 | Protocol state machine | Valid and invalid transitions with event/epoch handling | None |
| P06 | Version and capability negotiation rules | Unknown major/critical fields rejected; no downgrade | None |
| P07 | Canonical envelope schema draft | Logical field registry and validation, wire encoding choice explicitly deferred | None |
| P08 | Cross-language conformance fixture format | Deterministic input/expected-result structure and negative cases | None |
| P09 | Threat model and leakage matrix | Every role and operation lists disclosures and attacker capabilities | None |
| P10 | Mock-only end-to-end reference flow | Simulation clearly labeled as noncryptographic; exercises protocol state transitions | P01–P08 |
| P11 | SDK surface and documentation conventions | Language-neutral method signatures, typed failures and examples | P01–P08 |
| P12 | CI documentation/fixture validation | Markdown links, Mermaid syntax checks where tooling permits, JSON schema fixtures | P07–P08 |

These work items MUST NOT hard-code a final encryption scheme, proof system, ciphertext encoding, commitment hash, or key custody model.

## Decision gates

- **D1 — Completeness:** define who authenticates the full eligible rating set, how omission is detected, and how corrections/revocations work. Gate for sound aggregate proofs.
- **D2 — Trust/deployment:** decide issuer admission, operator/custodian collusion assumptions, and identity unlinkability. Gate for real deployments.
- **D3 — Crypto suite:** select authenticated encrypted aggregation, proof-friendly commitments, proof system, setup, and key lifecycle based on a measured prototype. Gate for production cryptography.
- **D4 — Canonical wire encoding:** pin deterministic bytes, registry numbers, domain separation and signature preimages. Gate for cross-language stable v1.
- **D5 — Privacy policy:** define public count/issuer leakage, freshness, revocation and presentation unlinkability. Gate for privacy claims.

## Milestones

1. **M0 — Planning baseline:** documentation, glossary, arithmetic, lifecycle, error taxonomy, logical messages, threat model and conformance framework. Exit: all undecided choices explicitly tracked.
2. **M1 — Decision-ready prototypes:** benchmark candidate crypto constructions and completeness designs, document threat/cost tradeoffs, accept ADRs. Exit: D1–D5 resolved.
3. **M2 — Protocol alpha:** normative serialization, credential and snapshot semantics, verified proof statements, Rust core with negative tests. Exit: independent verifier rejects all invalid fixtures.
4. **M3 — Interoperable beta:** WASM/TypeScript, Python and Go verification adapters, cross-language byte vectors, realistic reference marketplace. Exit: at least two independent implementations agree on vectors.
5. **M4 — Security release candidate:** external review, fuzzing, side-channel assessment, operational key recovery and migration tests. Exit: documented residual risks and resolved release-blocking findings.
6. **M5 — Stable v1:** immutable suite identifiers, published compatibility policy, reproducible conformance artifacts and release checklist.

## Parallel workstreams

- **Protocol:** P01–P08; owns logical semantics and schema drafts.
- **Security:** P09 and D1/D2/D5 analyses; owns threat model and security invariants.
- **Developer experience:** P10–P12; owns mock integration, docs and CI without implying secure implementation.
- **Crypto research:** D3 benchmarks and attack review; no production crypto merge until accepted ADRs.

## Definition of done

Every work item needs an owner, testable acceptance criteria, documentation link, negative test cases where applicable, and a review record. Cryptographic claims require a complete construction and independent review; no mock proof may be accepted by a real verifier. Track decisions in docs/adr and changes in CHANGELOG once releases begin.

## Immediate first sprint

Complete P01–P08, draft fixture schemas, and write mock verifier rejection tests. In parallel compare D1 designs; do not block language-neutral API work on D1.
