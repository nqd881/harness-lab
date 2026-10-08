# Idea

## Definition

A candidate opportunity, problem, or change worth investigating, before a
commitment to deliver a particular outcome. An Idea preserves intent and origin;
it is not a task, approved scope, or an imprecise Requirement.

Working classification: an entity when its investigation and disposition need
continuity over time. A fleeting suggestion may need only a note, not an Idea.

## Why this concept exists

The harness needs to distinguish possibilities from commitments, retain why work
was considered, and explain why an opportunity was pursued, deferred, or rejected.
Otherwise a suggestion can silently become mandatory scope, and rejected ideas
can repeatedly consume investigation without their rationale being available.

## Information

- Identity and revision history; short description of the opportunity or problem.
- Source, proposer, capture time, affected stakeholders, and intended scope.
- Desired outcome, expected value, assumptions, and known constraints.
- Investigation questions, alternatives, and supporting or challenging Evidence.
- Disposition, rationale, responsible human, and conditions for reconsideration.
- Links to derived Requirements and Decisions, including their specific revisions
  where a disposition relies on them.

Priority and value estimates are judgments, not proof. Uncertainty is permissible
and must not be disguised as a precise delivery promise.

## Lifecycle

Proposed states: `captured`, `exploring`, `deferred`, `pursued`, `rejected`.

- Capture enters `captured`; begin investigation moves `captured` or `deferred`
  to `exploring`.
- Defer moves `captured` or `exploring` to `deferred` with a reconsideration trigger.
- Pursue moves `captured`, `exploring`, or `deferred` to `pursued`.
- Reject moves `captured`, `exploring`, or `deferred` to `rejected`.
- Reopen moves `pursued` or `rejected` to `exploring`, preserving the old disposition.

`pursued` means authorized to develop commitments, not delivered. Deriving a
Requirement does not consume or transform the Idea; exploration may produce draft
Requirements before a pursuit decision. Consistency is separate from these states.

## Invariants

- A captured Idea identifies an opportunity and its source, even if the source is
  explicitly unknown. Duplicate captures can be linked without erasing provenance.
- Pursuit, rejection, and deferral record scope, rationale, actor, and authority.
- Pursuit identifies an intended outcome and who owns further exploration; it
  does not imply accepted Requirements or architecture.
- Deferral states why and when it should be reconsidered; a date is not mandatory.
- Evidence cited in a disposition identifies what claim it supports or challenges.
  No universal evidence threshold is assumed for low-cost investigation.
- Reopening preserves history and cannot silently revoke downstream commitments.
- Changing an Idea's assumptions marks dependent conclusions for review, not
  automatically rejected or withdrawn.

## Commands

Candidate command/event pairs (successful outcomes only):

| Command | Resulting event |
| --- | --- |
| CaptureIdea | IdeaCaptured |
| ReviseIdea | IdeaRevised |
| BeginIdeaExploration | IdeaExplorationStarted |
| DeferIdea | IdeaDeferred |
| PursueIdea | IdeaPursued |
| RejectIdea | IdeaRejected |
| ReopenIdea | IdeaReopened |

Each disposition command supplies rationale and authorized actor. Revisions that
change the basis of a disposition require re-evaluation, not silent reapproval.

## Events

The events above record completed domain changes, not requests or UI actions.
Disposition events identify the Idea revision considered, rationale, actor, time,
and cited Evidence. `IdeaPursued` must never mean `RequirementAccepted`.

## Relationships

- An Idea can motivate zero or many Requirements; a Requirement can have several
  motivating Ideas or arise directly from an external obligation.
- Decisions can authorize pursuit or resolve assumptions raised during exploration.
- An Architecture Baseline can provide feasibility context but normally traces
  commitments through Requirements and Decisions, not through an Idea alone.
- Questions expose unknowns; Evidence informs value and feasibility judgments.

## Authority

Proposed default: capture, drafting, and exploratory analysis may be performed by
humans or agents with permission. Pursue, defer, reject, and reopen require an
accountable human with product/scope authority. An agent may recommend these
transitions but must not manufacture authorization. The cost threshold at which
beginning exploration also needs human approval remains open.

## Open questions

See [I1-I3](../open-questions.md#idea): when an Idea warrants independent identity,
what pursuit commits to, and how duplicates, splits, and changes of intent behave.
The proposed states are dispositions, not a mandatory funnel for all development.
