# State and Authority

## Status of this model

Working recommendations from the first concept investigation. These are proposed
domain rules to test with scenarios, not policies already approved by stakeholders.
See [open questions](open-questions.md#state-and-revision).

## Separate dimensions

One status cannot distinguish authorization, compatibility, and fulfillment.

| Dimension | Question answered | Example |
| --- | --- | --- |
| Lifecycle/disposition | What has been proposed, authorized, or ended? | Requirement revision accepted |
| Consistency | Do the relevant dependencies and premises still agree in this context? | Accepted baseline needs review after a Requirement change |
| Satisfaction | Does this evaluated system meet this Requirement's criteria? | Requirement satisfied in one release, not satisfied in another |
| Conformance | Does actual structure match this accepted reference? | Deployed system differs from baseline |

Consistency findings are scoped assessments, not necessarily one permanent field
on each concept. Candidate outcomes:

- `unassessed`: no applicable assessment has been made.
- `consistent`: specified checks found no unresolved contradiction, within their
  stated coverage. This is not proof of universal correctness.
- `needs_review`: a premise changed, Evidence was challenged, or coverage is
  uncertain; no final conflict finding is implied.
- `inconsistent`: an identified contradiction exists for the stated context.

A change detection may move the applicable judgment to `needs_review`. A recorded
review can establish `consistent` or `inconsistent`; a further change reopens
review. Findings retain subject revisions, context, checks, rationale, actor,
time, and Evidence. How freshness and multiple conflicting findings are handled
remains open. Consistency does not decide whether a Question's answer is true.

## Revision and lifecycle

Requirements, Decisions, and baseline candidates have revision-specific review
and approval. Concept identity persists where the meaning remains continuous;
the boundary between a new revision and a new concept is not yet settled.

- Substantive edits to a draft create an identifiable revision. Reviewed content
  returns to draft/proposed before changes so reviewers know what changed.
- Acceptance/adoption binds exact content and premises. Creating a successor draft
  leaves the existing commitment in force until explicit replacement or ending.
- Accepted content is preserved; subsequent dispositions and assessments append
  history rather than rewriting what was accepted.
- Supersession requires an accepted/adopted successor, appropriate scope transfer,
  and authorized disposition of the predecessor. Rejection is not withdrawal.
- Known uncertainty can be an explicit reservation only where approval policy
  permits it. Blocking contradictions or unknown obligation meaning must not be
  relabeled as minor reservations to pass a guard.

These rules do not require synchronous acceptance of all related concepts or a
global project phase. Review is an activity; `in_review` is a state; the resulting
review report is an artifact and may supply Evidence.

## Human authority

The initial safety hypothesis reserves binding commitments and reversals for an
accountable human with a mandate covering the subject, scope, and transition:

| Subject | Human-authorized transitions | Relevant mandate |
| --- | --- | --- |
| Idea | pursue, defer, reject, reopen | Product/opportunity disposition |
| Requirement | accept, reject, withdraw, supersede | Obligation/scope authority |
| Decision | adopt, reject, revoke, supersede | Decision-kind and scope authority |
| Architecture Baseline | accept, reject candidate, retire, supersede | Architecture authority for the context |

An authorized human transition records actor, mandate, exact subject revision,
scope, rationale, time, and Evidence where required. Permission to edit is not
authority to approve. An agent can record an explicit human authorization without
being its source. Drafting, investigation, review requests, and review findings
may be delegated; returning content for revision follows the review mandate.

Automated checks can detect changes and publish observations. They cannot turn
an uncertain finding into human approval. Whether human endorsement is required
for a consistency or satisfaction judgment depends on consequences and risk;
release/compliance authorization is distinct from reporting a test result.
Exact delegation, quorum, external mandates, and escalation rules remain open.

## Transition guards and events

A command expresses requested intent. A successful lifecycle transition checks
source state, revision, scope, authority, required rationale, and Evidence policy.
Only then can its domain event assert that the change occurred. Denied requests
are not acceptance events. The command/event names in entity documents are
candidate vocabulary, not APIs, storage designs, or messaging requirements.

Shared consistency vocabulary: `FlagDependencyImpact` may produce
`DependencyImpactFlagged`; `RecordConsistencyAssessment` may produce
`ConsistencyAssessed`. These concern assessments, not automatic lifecycle changes.
