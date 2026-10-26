---
name: simple-implement
description: Implement a spec, ticket, or bounded change with focused validation and a final review. Use when the user requests implementation with minimal workflow and testing overhead.
---

Implement the requested work to its acceptance criteria, choosing the simplest adequate solution. Read applicable repository instructions and the relevant implementation before editing. Ask only about unresolved decisions that would materially change the result.

Use the current branch unless the user or repository requires another. Preserve unrelated changes. Implement directly; use TDD, additional review skills, or subagents when requested or required, rather than as mandatory stages.

## Validation

Run checks required by the user or repository. Otherwise, choose the smallest set of checks that gives meaningful evidence for the changed behavior and its affected callers:

- For a bug fix or consequential new logic, add or update a behavioral test when it provides useful regression coverage; reuse existing coverage where sufficient.
- For documentation, formatting, or similarly low-impact reversible changes, inspect the result and use an applicable formatter, validator, or smoke check rather than adding tests just for the change.
- Run focused tests during implementation when they resolve uncertainty or localize a likely failure. Batch checks across a coherent group of edits instead of running them after every edit or ticket. Run the relevant typecheck or build when changed code, types, or configuration warrant it.
- Use a full suite when required, when shared infrastructure or broad behavior changes, or when the affected area cannot be bounded with confidence. Otherwise use the affected tests and relevant integration checks.

Reuse passing results while the checked inputs, dependencies, and relevant configuration remain unchanged. After further edits, rerun the affected checks; a passing check from before those edits is not evidence for the changed behavior. Expand validation when failures or new evidence indicate wider impact. Once appropriate checks pass, stop testing unless something changes.

If a necessary check cannot run, report what prevented it and what remains unverified. Resolve failures introduced by the work; distinguish unrelated failures and avoid speculative repair loops or unrelated fixes.

## Finish

Review the task's final diff against the acceptance criteria and repository standards, including staged and unstaged task changes. Fix concrete defects, missing requirements, and unintended scope; recheck corrected areas without restarting the entire workflow.

Commit the task changes together on the chosen branch unless the user or repository specifies otherwise. Stage only changes belonging to this task. Report what changed, checks actually run and their outcomes, and any remaining blockers or verification gaps. Claim completion only when the requested work and required checks are complete.
