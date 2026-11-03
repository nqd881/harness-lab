# Refused Requirement Supersession

## Status and purpose

CR1-RS, investigated on 2026-10-23, follows
[CR1](changed-requirement-after-implementation.md). This is a hypothetical model
test, not a stakeholder Decision. It tests only the interval where R2 has been
accepted but a request to supersede R1 is refused. The policy branches below are
competing possibilities; neither is selected.

Reason for this investigation: the current model authorizes exact revisions and
requires explicit predecessor disposition, but does not define the successor's
present governing force between those actions. Calling both revisions `accepted`
cannot answer that question.

## Concrete setup

- Reuse CR1's planned search-service context C and unchanged workload W. Accepted
  R1 requires a response time of at most 500 ms; proposed R2 tightens it to 300 ms.
  They are revisions of the same Requirement by example assumption, not two newly
  introduced entities. The obligation is internally chosen.
- R1 initially governs C. No unrelated withdrawal, replacement, or change of
  context occurs during this walkthrough.
- Adopted Decision D1 retains the search structure using the margin against R1 as
  its rationale. Accepted baseline B1 fixes A1, D1, and R1 coverage. Neither fixes
  references to moving "latest" content.
- Evidence E1 measures system S1 at 420 ms under W. F1 records satisfaction of
  R1/S1/W; a separate finding records S1's structural conformance to B1.
- Priya retains CR1's mandate to accept and supersede this obligation for C. Arun
  retains architecture review/baseline authority, not obligation-disposition
  authority. Eva can assess Evidence and satisfaction; the agent can draft and
  flag impacts. No additional delegation is assumed.

The change from CR1 is at step 5: Arun requests supersession using Priya's R2
acceptance as supposed authorization. Priya has not authorized ending R1. The
request identifies the exact revisions and maps all of R1's C/W scope to R2;
missing scope mapping is not the reason for this particular refusal.

## Walkthrough

| Step | Action and guard | Result the model can state |
| --- | --- | --- |
| 1. Before acceptance | CR1's drafting, prospective review, and submission are complete; R2 is `in_review`. | R1 is accepted and governing. R2 is not governing. D1/B1 review against the proposal is prospective. |
| 2. Accept R2 | Priya requests `AcceptRequirement` for exact R2/C/W, with CR1's assumed adequate feasibility account and acknowledged S1 shortfall. Her mandate covers acceptance. | `RequirementAccepted`: R2 is accepted. R1 has not been superseded. The recorded approval does not say whether acceptance itself starts R2's governing force; the model leaves that policy open. |
| 3. Request replacement | Arun requests `SupersedeRequirement` for exact R1 with accepted R2 and complete whole-scope mapping. He cites R2 acceptance, not a separate human authorization of R1's disposition. | Revision and mapping guards can pass, but the authorization guard fails: architecture authority and successor acceptance do not authorize ending R1. |
| 4. Refuse the request | Priya checks the cited authority and declines to authorize this request. Record the request and its failed authority guard in this walkthrough. | No `RequirementSuperseded` success event occurs. R1 remains accepted and governing. R2 remains accepted; refusal neither rejects it nor rolls back its acceptance. No new refusal-event concept is assumed. |
| 5. Assess the new criterion | Eva requests `RecordSatisfactionAssessment` for R2/S1/W after confirming E1 applicability and coverage. | F2 is `not_satisfied`: 420 ms exceeds 300 ms. F1 and E1 remain unchanged. Whether this is a current governing-obligation shortfall or a future-obligation gap depends on the unresolved policy. |
| 6. Review dependencies | Arun reviews D1/B1 against exact R2 and records that its present force is unresolved. Any BC2 assembled as in CR1 remains draft. | D1 stays adopted; B1 stays accepted with R1/D1/A1 references. Their R2 support needs review, not automatic invalidation or replacement. Draft BC2 does not govern. |

Immediately before and after refusal, the lifecycle facts are the same: R1 and
R2 are both accepted revisions. R1 still governs because no authorized ending or
replacement has occurred in this example. The refusal supplies no new basis to
declare R2 governing or non-governing; that depends on what step 2 meant. In
particular, "R1 still governs" does not establish "only R1 governs."

## Unauthorized versus invalid requests

- **This request is unauthorized:** the accepted successor and complete mapping
  do not supply Arun with Priya's mandate or an explicit authorization to dispose
  of R1. Arun may propose replacement; his proposal cannot originate the binding
  authorization. R2 acceptance is not that authorization by implication.
- **A request could instead be invalid despite the right authority:** if Priya
  requested replacement of "the previous Requirement" without exact predecessor,
  accepted successor, and scope mapping, the missing revision/scope account would
  fail existing guards. Restoring authority alone would not repair that request.
- **Do not invent another guard:** S1 failing R2 or BC2 remaining draft is not,
  by itself, a stated supersession refusal condition in the current model. A
  stakeholder policy might add prerequisites, but this walkthrough cannot do so.

A failed supersession request is neither rejection of R2 nor withdrawal of R1.
It also does not establish that Priya's earlier acceptance was invalid. If a
later policy investigation challenges that acceptance, preserve what occurred
and expose the challenge rather than silently deleting the successful action.

## Competing policies for the same accepted history

### Possibility A: authorized successor, deferred governing force

Acceptance approves R2 as a future obligation. It does not begin governing C
until an explicitly authorized replacement takes effect, or another activation
condition explicitly established by the applicable policy is met. For this branch,
assume no such condition has been met before or after the refusal.

- Before acceptance, after acceptance, and after refusal, **R1 alone governs C**.
- **R2 can remain accepted and non-governing.** Its acceptance is still an
  accountable commitment to exact content, not a draft or an unapproved wish.
  The policy must explain what future commitment this creates, what starts its
  force, and whether an indefinite pending interval is allowed.
- Two accepted revisions coexist, but only one currently governs this scope.
  F2 describes a gap against the accepted future obligation, not failure of the
  presently governing R1 criterion.
- The current scope/conditions and authorization rationale can describe this
  branch, but the lifecycle labels alone cannot. The model has not defined an
  activation effect or condition sufficient to establish it.

### Possibility B: immediate additional obligation, separate predecessor ending

Acceptance for C makes R2 binding there immediately. Supersession would end R1's
governing force; it is not the act that begins R2's force. For this branch, assume
the policy permits overlapping accepted obligations, including these revisions.

- Before acceptance **R1 alone governs C**. After acceptance and after refusal,
  **both R1 and R2 govern C**. Refusal does not start R2's force; acceptance did.
- **R2 cannot be treated as non-governing merely because replacement failed.**
  Removing or deferring its current obligation would need the appropriate policy
  and authorization, not an agent's interpretation of the refusal.
- The obligations are compatible in this example: at most 300 ms under the same
  W also meets at most 500 ms. S1 nevertheless satisfies only R1. That numerical
  implication is not a general "newest wins" or "strictest wins" precedence rule.
- The per-revision lifecycle can describe the concurrent acceptances, but does
  not itself establish that concurrency is permitted or that acceptance activates
  this obligation. Those are premises of this branch, not discovered policy.

These branches disagree about R2's present force despite identical acceptance
and refusal history. If stakeholders instead require one accepted revision per
context and indivisible replacement, they must explain how the stipulated
successful R2 acceptance is handled; the current model has no such uniqueness
guard. That alternative cannot be imposed retroactively by pretending step 2
never happened. No branch is ratified by this investigation.

## Acceptance, applicability, and governing force

Three questions must be distinguished in explaining this case:

1. **Authorization:** was this exact obligation revision accepted, by whom, for
   which designated context and conditions? Yes for both R1 and R2 here.
2. **Scope/condition match:** does the context being considered fall within the
   Requirement's designated reach? C/W matches both statements here; that alone
   does not settle when R2 begins to bind.
3. **Present governing force:** must that obligation currently be honored in that
   context, on what policy/authorization basis, and alongside which obligations?
   R1 does; R2's answer differs between A and B.

"Applicable" is ambiguous if used for both the second and third questions. State
which meaning is intended. Here, activation means the beginning of governing
force; it is not a proposed entity, lifecycle state, or new command.

The case supports a conceptual distinction between accepted content and present
force. It does not establish that they need independent managed lifecycles:
stakeholders could couple them under a known policy, as B does. The current model
can preserve both acceptances, absence of scope transfer, exact dependency links,
and contextual findings. It cannot yet determine the complete governing set,
permitted duration of overlap, or how the effect of acceptance is established.
No first-class applicability or activation entity is needed to expose this gap.

There is also an acceptance-guard uncertainty: the model requires blocking
ambiguity about an obligation to be resolved, but does not say whether unspecified
governing effect is such a blocker. Missing policy information in this record is
not proof that the actors accepted a known ambiguity. If the effect was genuinely
undefined and should have blocked acceptance, stakeholders must classify and
resolve that earlier action explicitly. The accepted-history premise must remain
visible rather than being silently repaired by this walkthrough.

## What downstream Decisions and baselines should observe

Review must expose the accepted R2, the refused transfer and its reason, and the
unresolved governing effect, rather than just "Requirement changed."

| Concern | Under A | Under B | Common limit |
| --- | --- | --- | --- |
| D1's R1 margin rationale | Still addresses the current R1 obligation; review of the accepted future R2 remains relevant. | Cannot justify margin against the additional governing R2. | Keep D1's adopted content and old premise; neither refusal nor F2 proves the structural choice impossible. |
| B1's coverage | R1 coverage remains the current-obligation reference; R2 coverage is prospective. | R1 coverage is insufficient to claim coverage of both governing obligations; R2 needs an explicit review. | Preserve fixed references and acceptance; unestablished R2 support is not a demonstrated architectural contradiction. |
| F1 and F2 | F1 evaluates the current criterion; F2 evaluates the future criterion. | F1 and F2 evaluate different current criteria with different outcomes. | Do not merge verdicts, rewrite E1, or treat an evaluation as authority. |
| B1 and draft BC2 | Deferred R2 force does not itself authorize every use of B1. | Current R2 force does not automatically retire B1 or activate BC2. | Continued-use permission for B1 remains S2/W1; Requirement authority cannot supply architecture approval. |

Even before policy is selected, review can identify the R2 coverage/margin gap
and flag the affected claims `needs_review`, stating the uncertainty. It cannot
honestly summarize all current obligations as satisfied or all architecture as
inconsistent. The same accepted history has different consequences under A and B.

## Information an agent needs

A domain briefing must distinguish known facts, governing uncertainty, and the
authority needed to settle it. For this stopping point, a faithful briefing is:

> In C/W, R1 (500 ms) remains accepted and governing. Priya accepted exact R2
> (300 ms); Arun's whole-scope supersession request was refused for lack of
> obligation-disposition authority. No replacement occurred. R2's present governing
> force is unresolved because the acceptance-effect policy has not been supplied;
> do not report either that R2 is active or that R1 is the only governing revision.
> E1 records 420 ms for S1/W: F1 finds S1 satisfied R1; the new F2 finds S1 did not
> satisfy R2.
> D1/B1 retain their old revisions and premises; R2 support needs review. Any BC2
> is draft. Seek the missing policy determination and appropriate scoped human
> authorization before claiming replacement or a resolved governing set.

The explanation needs exact revisions, scope/conditions, acceptance authority,
the separate requested disposition and failed guard, any established activation
policy/conditions, and what remains unknown. "Accepted, non-governing under A" is
different from "accepted, governing effect unresolved"; absence of proof of
activation is not proof of non-activation. Neither "latest accepted" nor a bare
`accepted` label supplies this information. These are domain information needs,
not an API, storage format, or user-interface design.

The agent can continue scoped drafting, Evidence applicability checks, and impact
analysis. A conclusion or commitment that depends on R2 being current, or R1 being
exclusive, must expose the missing premise rather than silently choose a branch.

## Authority to resolve the situation

- **Choose acceptance-effect/coexistence policy:** an accountable stakeholder with
  a mandate to establish those rules for C must decide A, B, or another explicit
  alternative. Priya's stipulated acceptance/supersession mandate does not itself
  establish authority to set general policy. The example supplies no named holder
  of that policy mandate; delegation or joint authority remains W2/D3.
- **Complete this replacement:** Priya can explicitly authorize and request exact
  R1-to-R2 whole-scope supersession under her existing example mandate, subject to
  all guards. Refusal of Arun's request cannot substitute for that action. Under A,
  the applicable policy must also explain whether this action begins R2's force;
  under B, it ends R1 while R2 is already binding.
- **Retain, defer, or end R2 instead:** an obligation-scope authority must establish
  the permitted disposition under the selected policy. Do not silently undo its
  acceptance or call it rejected; ending an accepted obligation uses authorized
  withdrawal where allowed, and substantive content changes require a new draft.
- **Resolve downstream commitments:** Arun's architecture mandate covers baseline
  actions; any changed Decision needs its kind/scope authority. Eva's finding and
  the agent's report confer neither obligation nor architecture approval. Continued
  use of B1 needs whatever authority stakeholders establish, not an inferred waiver
  of R2.

## Remaining stakeholder questions

Under existing question IDs, obtain explicit answers on acceptance's governing
effect, permissibility of two accepted revisions in one context, pending/overlap
conditions and duration, and who may establish or change those rules (R2/S3/W1/W2).
Ask separately what B1 use remains permitted while R2's force or coverage is
unresolved (S2/W1). The walkthrough narrows these questions but resolves none of
them; see [open questions](../open-questions.md#cr1-rs-findings-refused-supersession).
