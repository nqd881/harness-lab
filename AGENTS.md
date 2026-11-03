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

## Git task-completion workflow

This is standing authorization to commit and push successfully completed work
units to dedicated task branches on `origin`. Apply it automatically before the
final task report; the user should not need to run Git commands or invoke
`/finish-task`. That command is an explicit way to request the same workflow.
Honor any newer user instruction and all required tool permissions/approvals.
This workflow does not authorize domain-policy decisions or application code.

### Before changing files

1. Inspect `git status --short --branch`, `git diff`, `git diff --cached`,
   `git remote -v`, and `git branch --show-current`.
2. Stop if there are unrelated uncommitted changes, conflicts, a detached HEAD,
   or an unexpected/missing `origin`. Report the exact blocker without altering
   existing work. Do not absorb pre-existing changes into the task.
3. Start each new work unit from a clean, agreed base on a new, uniquely named
   `task/<short-description>` branch using `git switch -c`. Record its starting
   commit and the intended scope. Resume an existing task branch only when its
   ownership and scope are established. Do not silently carry a previous task's
   commits into a new work unit; if the appropriate base is unclear, ask.

### After successful work, before reporting completion

1. Run checks appropriate to the task. For documentation, review consistency,
   scope, and links and run `git diff --check`. If verification fails or work is
   incomplete, stop before committing and report the problem.
2. Update `PROGRESS.md` for substantive domain work, retaining explicit
   uncertainties. Workflow-only work may record its setup and verification there.
   Preserve `domain_discovery` and `implementation.allowed: false` unless the
   user explicitly authorizes a project-phase change.
3. Inspect `git status --short --branch`, `git diff`, `git diff --cached`,
   `git log --oneline -10`, and the task diff from its recorded starting commit.
   Inspect new/untracked files too. Check every proposed file for credentials,
   tokens, private keys, sensitive data, generated files, and unintended changes.
   If any unrelated changes or suspected secrets appear, stop and report them.
4. Confirm the current branch is the task's `task/*` branch and `origin` is the
   intended GitHub repository. Never automatically commit or push on `main` or
   any other non-task branch. Stage only explicit task-owned paths with
   `git add -- <paths>`; never use blanket staging (`git add .` or `git add -A`).
5. Review `git diff --cached --check`, `git diff --cached --stat`, and the full
   `git diff --cached` again for secrets and scope before committing. If there
   is no task diff, report a no-op; do not create an empty commit.
6. Create a meaningful, concise commit matching the repository's style. Honor
   hooks; never skip them. If a hook fails, inspect its effects and fix only
   task-owned problems, reverify, restage, and retry with a new commit command.
   Do not amend existing commits automatically.
7. Inspect the resulting commit and worktree. Push only the verified task branch
   using `git push --set-upstream origin HEAD:refs/heads/task/<actual-name>`
   (substitute the exact current branch). Never force-push, reset, discard work,
   bypass approvals, or automatically merge a pull request. Stop on conflicts,
   non-fast-forward rejection, authentication failure, or permission denial;
   preserve any local commit and report the exact blocker.
8. After a successful push, verify that `git ls-remote --heads origin
   refs/heads/task/<actual-name>` reports the same hash as `git rev-parse HEAD`.
   Report the branch, commit, checks performed, and push result. Do not claim
   remote success without confirmation. Leave the task branch checked out.

Run this workflow once at successful task completion, not on each file edit,
assistant turn, or `session.idle` event. Read-only tasks with no changes need no
commit. This is agent-directed automation, not an unconditional event hook;
permissions and agent adherence still determine whether it executes.
