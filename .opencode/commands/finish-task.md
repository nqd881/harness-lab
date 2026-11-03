---
description: Verify completed work, commit task-owned changes, and push the task branch
agent: build
---

Complete the current work unit using the Git task-completion workflow in
`AGENTS.md`. Read the repository instructions and current project state first.

Task context supplied by the user: $ARGUMENTS

Establish the task branch, starting commit, and owned paths from the current
session before staging anything. If ownership or the base cannot be established,
stop and explain the blocker. Do not treat every dirty file as task-owned.

Verify the work, inspect all changes for scope and secrets, update `PROGRESS.md`
for substantive domain work, stage explicit paths, review the staged diff,
commit, push the task branch to `origin`, and confirm the remote commit hash.
Honor required permissions and all stop conditions in `AGENTS.md`.

Report the branch, commit, verification results, and confirmed push status or
exact blocker. Preserve the project's domain-discovery restrictions.
