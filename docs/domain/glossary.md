# Harness Domain Glossary

This glossary contains the ubiquitous language of the harness domain.

Terms are exploratory until explicitly stabilized.

## Idea

A candidate opportunity, problem, or change worth investigating, not a delivery
commitment. Pursuit authorizes further development of commitments, not fulfillment.

## Requirement

A statement describing behavior, capability, quality, or constraint
that a system is expected to satisfy in an explicit scope and context. Acceptance
authorizes an obligation at a particular revision; implementation and satisfaction
are separate concerns. Whether successor acceptance begins its governing force
immediately or approves a future obligation remains an unresolved policy question.

## Requirement Applicability and Governing Force

Scope/condition match asks whether a context is within a Requirement's designated
reach. Governing force asks whether the exact obligation binds there now, and on
what authority/policy basis. "Applicable" must state which meaning is intended.
Activation denotes the beginning of governing force, not a new entity or proposed
lifecycle state. CR1-RS tests separate acceptance and present-force questions;
their coupling and permitted coexistence remain open.

## Decision

A recorded, scoped resolution of a meaningful question, including outcome,
rationale, and authority. Before adoption it is a proposed resolution. Product,
domain, architecture, and governance are candidate kinds, not settled subtypes.

## Architecture Baseline

An accepted, versioned reference configuration of architecture descriptions and
applicable Decisions for a particular system scope and context. It is not the live
architecture or proof of implementation conformance. `ArchitectureBaseline` is
the compact concept name for Architecture Baseline.

## Architecture Description

A representation of intended structure, responsibilities, interactions, and
constraints. Multiple descriptions can contribute to a baseline; being a
description does not by itself imply independent entity identity.

## Baseline Candidate

A proposed reference configuration awaiting acceptance. Whether it and an
accepted baseline have one identity or distinct identities remains open.

## Question

Explicit unresolved uncertainty, scoped to the matter needing clarification.
A Question is not a discussion activity or a proposed Decision.

## Evidence

Identifiable information offered to support or challenge a specific claim in a
stated context. Evidence can be inconclusive; its existence does not prove a
claim or confer authority. First-class identity is a working recommendation when
provenance, reuse, and reassessment matter.

## Revision

An identifiable version of a concept's substantive content. Accepted content is
preserved; a new candidate revision does not inherit acceptance. Entity identity
and revision identity answer different questions.

## Trace Link

A meaningful relationship, such as motivates, constrains, addresses, or supports,
with direction, scope, and relevant endpoint revisions. An association is not
automatically a dependency or proof of fulfillment. Independent link identity
remains under investigation.

## Actor and Authority

An Actor performs an action. Authority is the mandate to authorize a particular
transition for a scope; it is not implied by authorship, expertise, or access.
The current safety hypothesis requires accountable human authority for binding
commitments and their reversal. Delegation and joint approval rules remain open.

## Lifecycle State

Where a revision or disposition stands in its authorized workflow, such as draft,
accepted, or withdrawn. It does not summarize correctness, delivery, or validity.

## Consistency Assessment

A contextual judgment about compatibility with current dependencies and premises.
Candidate outcomes are unassessed, consistent, needs review, and inconsistent.
An upstream change can trigger review without revoking acceptance.

## Satisfaction Assessment

An evaluation of whether a particular system revision in stated conditions meets
a Requirement revision's criteria, supported by Evidence. A contextual finding,
not the Requirement's lifecycle or an implementation progress status.

## Conformance Assessment

An evaluation of an actual system's structure against an Architecture Baseline
in a specified context. It does not substitute for Requirement satisfaction.

## Command and Domain Event

A command requests an action and can be refused when its guards fail. A domain
event records an action or change that occurred; proposed event names in these
documents are discovery vocabulary, not an implementation specification.

## Invariant

A condition that must remain true for a domain object or transition
to be valid.

## Transition

A valid change from one domain state to another.
