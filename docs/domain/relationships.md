# Domain Relationships

Working hypotheses, not a fixed ownership or aggregate model. Links describe
meaning and applicability; arbitrary connectivity does not imply change impact.

## Relationships and their limits

| Relationship | Meaning | What it does not imply |
| --- | --- | --- |
| Idea motivates Requirement | Explains an obligation's origin or intended value | Pursuing an Idea accepts the Requirement |
| Decision governs Idea disposition | Records a consequential pursuit/defer/reject choice | Every disposition needs a separate Decision entity |
| Requirement raises Question | Exposes ambiguity, conflict, or feasibility uncertainty | Every Requirement must have a Question |
| Decision resolves Question in a scope | Selects an authorized outcome | All contexts of the Question are resolved |
| Decision constrains Requirement | Establishes interpretation or scope rationale | Adoption automatically changes an accepted obligation |
| Requirement constrains architecture | States what architecture must accommodate | A design or passing test fulfills all criteria |
| Baseline addresses Requirement revision | Records architectural response and coverage | Coverage proves satisfaction |
| Baseline incorporates Decision revision | Fixes applicable choices and consequences | All Decisions are owned by that baseline |
| Baseline fixes description revisions | Provides an accepted architectural reference | Descriptions or deployed systems cannot evolve independently |
| Evidence supports/challenges claim | Gives grounds for a contextual judgment | Evidence authorizes a transition or is always conclusive |
| Assessment evaluates scoped subject | Records consistency, satisfaction, or conformance findings | Findings change the subject's lifecycle automatically |

Each core concept can have zero or many links during discovery. Requirements may
originate from external obligations without an Idea. Ideas can motivate multiple
Requirements, and a Requirement can have multiple motivating Ideas. Neither a
linear Idea-to-Requirement-to-Decision-to-Baseline funnel nor a universal global
phase is assumed. Requirements and Decisions may constrain each other; such a
relationship is not a circular argument unless each uses the other as its sole
justification.

## Revision and scope discipline

- Links used in an acceptance or adoption refer to identifiable revisions and
  applicability contexts, not moving "latest" content.
- A general exploratory association can remain concept-level; it must become
  precise when used as a premise of a binding transition.
- Origin links (such as motivates) and premise links (such as depends on an
  assumption) have different impact rules. Rejection of an originating Idea does
  not automatically withdraw an independently justified Requirement.
- Replacements preserve history and explicitly describe scope transfer. For
  partial replacement, unresolved obligations cannot vanish in an unqualified
  supersession link.
- Baseline inclusion does not imply ownership of Requirements, Decisions,
  descriptions, or Evidence. Aggregate boundaries remain an open question.

## Change propagation

1. Record an upstream revision, changed assumption, withdrawal, or challenged
   Evidence with its reason and affected scope.
2. Identify dependent claims using relevant link meanings and applicability.
   Record why each may be affected; do not mark every reachable artifact invalid.
3. Flag affected judgments `needs_review`. Preserve accepted/adopted lifecycle
   records and governing references while the impact is uncertain.
4. Assess each dependency against the changed premise. Record Evidence and a
   reasoned finding: unaffected/consistent, inconsistent, or still unresolved.
5. Where a commitment must change, use its authorized revise, withdraw, revoke,
   retire, or supersede transition. Cascading lifecycle changes need their own
   authority; they are not side effects of a graph update.

Example: Requirement R revision 2 tightens a response-time criterion while R1
remains accepted during review. Accepting R2 with explicit supersession of R1
flags Decision D and baseline B if their choices depended on the old criterion.
B remains an accepted historical reference, possibly `needs_review`. A finding
that B cannot support R2 makes it `inconsistent` for that context, not silently
retired. Its successor needs architecture approval. Test Evidence for a build
against R1 cannot establish satisfaction of R2 without reassessment.

## Authority boundaries

Product/scope authority accepts obligations; decision authority depends on kind
and scope; architecture authority accepts a reference configuration. One human
may hold several mandates, but one approval does not implicitly exercise all of
them. Cross-scope changes expose additional required approvals and conflicts.
See [state and authority](state-and-authority.md) and unresolved questions W1-W2.
