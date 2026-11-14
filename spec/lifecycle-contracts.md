# Lifecycle contracts — draft

## Authorization
Created -> issued -> consumed OR expired/revoked. An authorization MUST NOT be consumed twice within its defined scope.

## Contribution
Submitted -> validated -> included OR rejected. Inclusion MUST refer to an authenticated snapshot. A correction creates an auditable replacement or revocation event rather than silently mutating a committed historical snapshot.

## Snapshot
Collecting -> committed -> active -> superseded/expired. Disputed and corrected states may require a new snapshot; proof verification MUST check the epoch and policy version.

## Presentation
Requested -> generated -> verified OR rejected/expired. A presentation is audience/challenge scoped and MUST NOT silently carry over to a different verifier.

State transitions MUST be explicit, idempotent where appropriate, and independently testable. Snapshot governance and dispute policy remain undecided.
