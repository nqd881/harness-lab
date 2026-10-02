# Agent Instructions

## Purpose

This repository is being used to discover and model the domain of a
software-development harness.

We are NOT currently implementing the harness application.

The current goal is to understand the domain well enough that an
implementation can later be derived from it.

## Start every session by reading

1. `PROJECT_STATE.yaml`
2. `PROGRESS.md`
3. `docs/domain/glossary.md`
4. Relevant files under `docs/domain/`

Do not assume conversation history is authoritative project state.

Persist important knowledge in the repository.

## Current scope

We are modeling concepts involved in managing software development.

Current core candidates include:

- Idea
- Requirement
- Question
- Decision
- Architecture Baseline
- Evidence
- Revision
- Trace Link
- Actor / Authority

These are hypotheses, not fixed design.

Challenge them when appropriate.

## Domain discovery rules

Do not jump directly to database schemas, APIs, classes, frameworks,
microservices, or implementation.

Prefer questions such as:

- What does this concept mean?
- Why does it exist?
- What information belongs to it?
- What lifecycle does it have?
- What invariants apply?
- What commands change it?
- What events result?
- What other concepts depend on it?
- What evidence is needed for a transition?
- Who has authority to perform the transition?

Distinguish carefully between:

- domain entity;
- value/object concept;
- lifecycle state;
- activity/process;
- artifact;
- evidence;
- event;
- command.

For example, "Draft" may be a state rather than an entity, and
"Discussion" may be an activity rather than a core entity.

## Modeling discipline

Do not treat the existing model as correct merely because it already
exists.

Record disagreement and uncertainty in:

`docs/domain/open-questions.md`

Do not silently resolve important ambiguity.

## Changes

When modifying a domain concept:

1. explain the reason;
2. consider effects on related concepts;
3. update relationships/invariants when necessary;
4. update `PROGRESS.md`;
5. leave unresolved questions explicit.

## Current implementation restriction

Do NOT create application source code unless `PROJECT_STATE.yaml`
explicitly changes the project into an implementation phase.

For now, work only on domain discovery and modeling.