---
name: fast-implement
description: Implement a specified feature directly from the user's request with minimal validation and no branch creation. Use when the user wants a fast implementation without a spec or ticket workflow.
---

Implement the feature described by the user. This skill is self-contained: use the request and relevant project context directly, without requiring or generating specs, tickets, or issue-tracker setup.

## Implement directly

Read applicable repository instructions and inspect the relevant entry point and nearby patterns. Reuse known context; expand exploration only to answer a concrete implementation question. Ask only if a missing decision would materially change the requested behavior; choose simple defaults for minor reversible details.

Work in the existing checkout on its current branch. Do not create or switch branches, create worktrees, or merge branches. Preserve unrelated local changes. Git setup is unnecessary when working outside a repository.

Make the smallest coherent change that completes the requested behavior. Reuse existing code and conventions; keep refactoring limited to what the feature needs. Implement directly without mandatory TDD, review-skill calls, subagents, or planning documents.

## Minimal validation

Inspect the final task diff for missing behavior, obvious defects, and unintended edits. Then choose the cheapest meaningful evidence for the changed behavior: normally a focused existing test, a direct smoke check, or a relevant static check. For prose-only or similarly trivial changes, inspection or an applicable validator may suffice.

Run checks explicitly required by the user or repository. Otherwise:

- Batch validation after coherent edits rather than after each file change. Select checks for distinct uncertainties; avoid stacking tests, typechecks, builds, and browser runs that establish the same thing.
- Reuse existing coverage. Add a small behavioral regression test only when changed logic or a demonstrated bug warrants it; low-impact edits need no new tests merely to accompany the change.
- Run a full suite only when concrete evidence shows focused checks cannot adequately cover the impact. Broaden checks to resolve an identified concern, rather than as a routine final stage.
- Reuse passing results while relevant inputs remain unchanged. After a correction, rerun affected checks; once the requested behavior and necessary checks are satisfied, stop validating.

Fix failures introduced by the change. If validation is blocked by the environment or an unrelated failure, report the specific gap; avoid unrelated repairs or repeated unchanged retries.

## Deliver

Briefly report what changed, validation actually performed and its outcome, and any unverified behavior or blockers. Leave changes in the working tree by default; commit, push, or open a PR only when requested. Completion means the requested feature is implemented and required checks pass; report incomplete work or blocked verification explicitly.
