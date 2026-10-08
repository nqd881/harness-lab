# Decision

## Definition

A recorded, scoped resolution of a meaningful question, including the selected
outcome, rationale, and authority. Before adoption it is a proposed resolution;
the unresolved Question and the activity of deliberation are distinct concepts.

Working classification: an entity for consequential resolutions whose authority
and continuing applicability must be traceable. Not every preference, comment,
or computed result warrants a Decision record.

## Why this concept exists

The harness must distinguish recommendations from authorized choices, preserve
rejected alternatives and tradeoffs, and explain which commitments depend on a
choice. Without this record, later changes can reuse a conclusion after its
assumptions have failed or reopen settled questions without their original basis.

## Information

- Identity, revision, question being resolved, and explicit scope/applicability.
- Candidate kind: product/scope, domain interpretation, architecture, or governance.
- Options considered, selected outcome, rationale, tradeoffs, consequences, and
  known risks. A forced external choice may explain why no alternatives exist.
- Assumptions, relevant Requirement and baseline revisions, supporting and
  challenging Evidence, and unresolved Questions.
- Proposer, accountable deciding human, authority basis, adoption time, review
  triggers, and links to replaced Decisions.

Working recommendation: retain one common Decision concept with kinds and
kind-specific authority/evidence expectations. Kinds are not lifecycle states.
An approval act (for example, accepting a Requirement) is always recorded as part
of that transition; a separate Decision is useful when there is a consequential
question or tradeoff, not mandatory duplicate paperwork for every approval.

## Lifecycle

Proposed states per resolution revision: `proposed`, `in_review`, `adopted`,
`rejected`, `revoked`, `superseded`.

- Propose enters `proposed`; submit enters `in_review`.
- Return for revision moves `in_review` to `proposed` before substantive editing.
- Adopt or reject moves `in_review` to `adopted` or `rejected`.
- Revoke moves `adopted` to `revoked` without replacement; supersede moves it to
  `superseded` when an adopted successor covers its scope.
- Reconsideration creates a new proposal linked to the old resolution. The old
  resolution is not silently unadopted while alternatives are discussed.

`adopted` means authorized, not universally true or still applicable to every
context. Failed assumptions affect consistency and applicability separately.

## Invariants

- Review identifies a meaningful question, scope, proposed outcome, rationale,
  alternatives or why they are unavailable, and known consequences.
- Adoption identifies the exact resolution revision, responsible human, authority
  basis, and relevant Evidence. No unresolved blocker may be hidden as a settled
  premise; permitted risks or reservations are explicit.
- Evidence of a tradeoff informs a choice; it cannot confer deciding authority.
- Adoption does not automatically accept Requirements or activate a baseline.
  Those transitions have their own guards and may need different human authority.
- Adopted content, rationale, and premises remain historical records. A changed
  conclusion requires a new proposal; editorial corrections must be distinguishable.
- Supersession identifies an adopted successor with overlapping scope and explains
  how commitments migrate. Revocation states why the resolution no longer governs.
- Incompatible adopted resolutions in overlapping scope trigger an explicit
  conflict. Later timestamps alone do not resolve the conflict.
- Loss of supporting Evidence triggers impact review, not automatic revocation.

## Commands

Candidate command/event pairs:

| Command | Resulting event |
| --- | --- |
| ProposeDecision | DecisionProposed |
| ReviseDecisionProposal | DecisionProposalRevised |
| SubmitDecisionForReview | DecisionReviewRequested |
| ReturnDecisionForRevision | DecisionReturnedForRevision |
| AdoptDecision | DecisionAdopted |
| RejectDecision | DecisionRejected |
| RevokeDecision | DecisionRevoked |
| SupersedeDecision | DecisionSuperseded |

Reconsidering an adopted choice uses ProposeDecision with a predecessor link.

## Events

Events identify the resolution revision and scope. Adoption, rejection,
revocation, and supersession record who decided, under what mandate, why, when,
and on which premises. `DecisionAdopted` is neither proof of correctness nor proof
that its consequences have been implemented.

## Relationships

- Decisions may govern Idea dispositions, Requirement interpretation or scope,
  and architecture choices; none of these relations is mandatory for every Decision.
- A Question can have competing proposed resolutions and different adopted
  resolutions for non-overlapping contexts. Resolving it requires scope coverage,
  not merely the existence of one Decision link.
- Requirements constrain architecture choices; Decisions can justify a proposed
  change but cannot silently waive an accepted obligation.
- An Architecture Baseline references applicable adopted Decision revisions and
  captures their structural consequences, rather than containing all Decisions.
- Evidence supports or challenges premises and option comparisons.

## Authority

Agents can propose options, collect Evidence, and flag conflicts. Adopt, reject,
revoke, and supersede require an accountable human authorized for the decision's
scope and kind. Product authority does not automatically imply architecture or
compliance authority. Returning a proposal for revision follows the review mandate.
Cross-scope Decisions may need multiple approvals; the quorum and escalation model
are deliberately unresolved. External mandates need provenance and local handling,
not an invented local decision-maker.

## Open questions

See [D1-D3](../open-questions.md#decision): when kinds require distinct concepts,
approval records versus substantive Decisions, and joint/external authority.
One common concept is provisional; differing reversibility or binding force may
justify a split once concrete workflows demonstrate it.
