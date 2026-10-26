---
name: simple-implement-spec
description: Implement a complete spec and its dependent tickets on one branch with shared validation. Use when delivering multiple tickets without a branch, worktree, and merge cycle for each ticket.
---

Read the spec, acceptance criteria, and available tickets. Treat ticket dependencies as an execution order. If tickets or issue-tracker configuration are absent, derive a small execution checklist from the spec rather than requiring tracker setup.

Read [simple-implement](../simple-implement/SKILL.md) once and apply its implementation, validation, review, and commit policy to the whole spec as one delivery. Use the user- or repository-required branch; otherwise stay on the current branch. Keep the starting revision and pre-existing local changes identifiable so the final review covers only this task.

Implement ready tickets directly in dependency order on that branch. Group closely related tickets when they touch the same behavior. Use separate branches, worktrees, or parallel agents only when requested by the user or required by the repository. A ticket boundary alone is not a reason to switch branches, merge, commit, or rerun checks.

Track which acceptance criteria are implemented, which checks cover them, and any blockers in the existing ticket list or working checklist. Run a focused check sooner when a dependent ticket relies on uncertain behavior. Share passing validation across tickets while its inputs remain unchanged, and check interactions between tickets as part of final validation.

After implementation, review the combined task diff and run the remaining necessary checks. Correct concrete issues in place and rerun affected checks. Finish with one combined task commit by default, following simple-implement; user or repository requirements may specify another commit structure.

Follow the user's authorized PR and issue-tracker workflow when one is provided; otherwise report ticket completion locally. Mark work complete only when its acceptance criteria and required checks are satisfied. Report the branch, delivered tickets, checks actually run, and any incomplete or unverified work.
