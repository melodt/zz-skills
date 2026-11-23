---
name: verified-simple-implement-spec
description: Implement a complete spec and its dependent tickets using simple-implement-spec practices with documented ticket and integrated test-case verification.
---

# Verified Simple Implement Spec

Read the sibling [test-case-workflow](../test-case-workflow/SKILL.md), [simple-implement-spec](../simple-implement-spec/SKILL.md), and its sibling [simple-implement](../simple-implement/SKILL.md). Install all four directories together. Apply their implementation, dependency, focused validation, review, and commit practices subject to the gates below and applicable user and repository instructions.

1. Read the spec, acceptance criteria, available tickets and detailed design. If tickets or tracker configuration are absent, derive a small checklist from the spec as the original skill specifies. Before implementation, generate or update one feature case document mapping cases to applicable tickets or checklist items and cross-item scenarios. Record missing sources and unresolved expectations.
2. Implement ready work in dependency order on the user- or repository-required branch, otherwise the current branch. Group related work and share valid evidence across items; a ticket boundary alone does not require a branch, commit, or repeated check. Track case IDs, acceptance criteria and blockers. Continue independent work when possible.
3. Verify each item's applicable cases against its relevant version before any action that completes or closes that item. Then review the combined diff and verify cross-item and integration-affected cases on the final integrated version. Reassess and rerun evidence invalidated by changes. Run other checks required by the user or repository.
4. Apply the mandatory [implementation status write-back](../test-case-workflow/references/implementation-status.md) before reporting or final completion actions, including partial or blocked work. Only declare the approved spec scope verified and perform its authorized final completion actions after all applicable cases pass with evidence and required write-backs succeed. Failed, blocked, pending, unexecuted or stale cases prevent their affected completion actions. If the user explicitly approves a narrower scope, report excluded cases and do not claim the original spec passed.

Apply the original single-delivery commit policy only after the integrated gate and subject to user and repository instructions. Do not invoke either original skill as an opaque workflow that could commit or close work before the relevant gate. Report per-item and integrated results, evidence, blockers and exclusions.
