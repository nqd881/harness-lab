# Requirement

## Definition

A scoped statement of expected behavior, capability, quality, or constraint.
An accepted Requirement is an authorized obligation for a particular revision
and designated context. A draft proposes such an obligation. Whether acceptance
of a successor makes it govern immediately or authorizes future governing force
remains unresolved; acceptance does not by itself establish predecessor disposition.

Working classification: an entity whose identity can persist across revisions.
Acceptance criteria describe what would satisfy it; they are not implementation
tasks, test executions, or proof that it has been satisfied.

## Why this concept exists

The harness needs an explicit account of what the system is expected to satisfy,
why that expectation exists, who authorized it, and how fulfillment could be
judged. This separates scope agreement from delivery activity and prevents code
completion from being mistaken for compliance with the agreed outcome.

## Information

- Identity, revision, statement, rationale, and obligation source.
- Scope and applicability: system boundary, stakeholders, conditions, and relevant
  release or operating context when known.
- Basis for present governing force in that context, including any established
  activation conditions or unresolved overlap with other accepted revisions.
  Designated scope and current force must not be silently conflated.
- Acceptance criteria or a justified evaluation method, including measurable
  thresholds for quality expectations where appropriate.
- Assumptions, constraints, priority, and dependencies on other Requirements.
- Owner, accepting authority, acceptance rationale and time, cited Evidence, and
  any explicit reservations with owners and disposition conditions.
- Relationships to motivating Ideas, governing Decisions, architecture coverage,
  replacement Requirements, and satisfaction assessments.

Implementation activity belongs elsewhere. A satisfaction assessment refers to
a Requirement revision, a system/build or release context, evaluation conditions,
criteria assessed, outcome, assessor, time, and Evidence. Proposed outcomes are
`not_assessed`, `partially_satisfied`, `satisfied`, `not_satisfied`, and
`inconclusive`; these are not Requirement lifecycle states. Whether the assessment
is a separate entity remains open (R1).

## Lifecycle

Proposed states per revision: `draft`, `in_review`, `accepted`, `rejected`,
`withdrawn`, `superseded`.

- Propose creates `draft`; submit moves `draft` to `in_review`.
- Return for revision moves `in_review` to `draft`.
- Accept or reject moves `in_review` to `accepted` or `rejected`.
- Withdraw moves `accepted` to `withdrawn` when the obligation is ended without
  replacement; supersede moves it to `superseded` when an accepted replacement
  explicitly takes over its scope.
- Rejected or accepted content is reconsidered through a new draft revision;
  historical acceptance or rejection is retained. A revision in review must be
  returned to draft before substantive edits.

A new draft does not replace the accepted revision. An accepted Requirement may
remain unimplemented, satisfied in one release, unsatisfied in another, and
`needs_review` after a dependency change. These facts must not be collapsed into
one status. Draft abandonment and partial scope replacement need further study.

The [refused-supersession follow-up](../scenarios/refused-requirement-supersession.md)
can describe two accepted revisions after a failed replacement request. The current
per-revision lifecycle neither forbids that coexistence nor determines whether
both govern. An accepted, non-governing successor is one policy possibility, not
an established state or universal rule. The competing possibility makes acceptance
immediately binding alongside the predecessor until an authorized ending.

## Invariants

- Review submission identifies the expected outcome, scope, source, criteria or
  evaluation method, and known unresolved Questions.
- Acceptance records the exact revision, authorized human, rationale, and applicable
  scope. Blocking ambiguity about the obligation must be resolved; permitted
  reservations are explicit, not silently treated as satisfied criteria.
- Acceptance needs a reasoned account of desirability, evaluability, and relevant
  feasibility risks. The required Evidence depends on risk; passing implementation
  tests are not a prerequisite to accepting a future obligation.
- Accepted content and its acceptance record are not overwritten. Substantive
  changes create a candidate revision and trigger impact review.
- Conflicting accepted obligations in overlapping scope cannot be presented as
  reconciled without an authorized Decision or explicit unresolved conflict.
- Supersession names an accepted successor revision and scope mapping. It must not
  silently drop part of an obligation; partial replacement remains unresolved.
- Successor acceptance is not proof that predecessor scope transfer occurred. A
  refused supersession changes neither revision's lifecycle by itself and does
  not reject or undo an earlier valid acceptance.
- Claims about which revisions govern identify their scope and authorization/policy
  basis, or explicitly leave the effect unresolved. Neither "latest accepted" nor
  acceptance alone proves exclusive governing force. Two accepted revisions are
  not necessarily conflicting, nor is their concurrent force established by their
  lifecycle labels.
- Withdrawal records authority and reason and triggers dependent review; it is
  neither proof of fulfillment nor retroactive erasure of a past obligation.
- Satisfaction claims identify exact Requirement and evaluated system revisions,
  criteria coverage, conditions, and Evidence. No claim transfers automatically
  to a changed Requirement or a different release.
- Existing observations may support a new assessment after explicit applicability
  and coverage review. Reusing Evidence does not reuse an old verdict or rewrite
  the original assessment; a stricter criterion can yield a different finding.

## Commands

Candidate command/event pairs:

| Command | Resulting event |
| --- | --- |
| ProposeRequirement | RequirementProposed |
| ReviseRequirement | RequirementRevised |
| SubmitRequirementForReview | RequirementReviewRequested |
| ReturnRequirementForRevision | RequirementReturnedForRevision |
| AcceptRequirement | RequirementAccepted |
| RejectRequirement | RequirementRejected |
| WithdrawRequirement | RequirementWithdrawn |
| SupersedeRequirement | RequirementSuperseded |
| RecordSatisfactionAssessment | RequirementSatisfactionAssessed |

The last command acts on a related assessment, not the Requirement's lifecycle.

## Events

Events identify the affected revision and context. Acceptance, rejection,
withdrawal, and supersession also preserve rationale and authority. A
`RequirementSatisfactionAssessed` event records an evaluation outcome, not a
scope approval or universal declaration that the Requirement is "done."

## Relationships

- Ideas may motivate Requirements but are not mandatory origins.
- Decisions settle scope, resolve conflicts, approve exceptions, or constrain
  interpretation; a Decision is not itself automatically a Requirement.
- Architecture Baselines identify how and where Requirement revisions are
  addressed, and disclose gaps. Architecture coverage is not satisfaction proof.
- Requirements can depend on, refine, or conflict with other Requirements; each
  link has a meaning and scope, not just an undirected association.
- Evidence supports feasibility claims and satisfaction assessments separately.

## Authority

Drafting, trace suggestions, and evaluation runs may be delegated to agents.
Accept, reject, withdraw, and supersede require an accountable human with authority
over the obligation's scope. A reviewer can return a proposal for revision under
the review mandate; whether an agent can do this is a policy question.
Automated tests may produce assessment Evidence but do not accept Requirements.
High-risk compliance or release acceptance may additionally require a human to
endorse the satisfaction judgment; that is not the same authority as scope approval.

## Open questions

The [CR1 walkthrough](../scenarios/changed-requirement-after-implementation.md)
supports separate satisfaction records for changed criteria and system revisions,
without establishing independent assessment entity identity. It also exposes the
unsettled distinction between successor acceptance and completed scope transfer.
CR1-RS tests refusal and distinguishes authorization, scope/condition match, and
present governing force without deciding whether they need independent lifecycles.

See [R1-R4](../open-questions.md#requirement): assessment identity, contextual
applicability, obligation sources and waivers, and refinement/partial supersession.
Separating implementation status is a working recommendation, not a decision that
the harness must own a delivery-work entity.
