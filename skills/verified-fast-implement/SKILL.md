---
name: verified-fast-implement
description: Implement a bounded feature with fast-implement practices and a documented test-case completion gate. Use when a quick implementation must be verified against traceable functional cases.
---

# Verified Fast Implement

Read the sibling [test-case-workflow](../test-case-workflow/SKILL.md) and [fast-implement](../fast-implement/SKILL.md). Install all three directories together. Follow fast-implement's direct, minimal-change workflow and current-checkout restrictions, with the test-case preparation and verification requirements below. User instructions and repository rules remain applicable.

1. Read the request, relevant project context and available spec, ticket or detailed design. Before implementation, prepare or update cases under the shared workflow and identify the applicable scope. This verified variant needs at least one readable source of those three kinds: a request alone does not meet the shared workflow's formal-case requirement. If none exists, report the missing source, stop formal case generation, and continue authorized independent implementation where possible; do not create a spec or ticket merely to bypass the requirement. Verification and completion actions remain blocked until an eligible source and passing cases are available.
2. Implement directly in the current checkout without creating or switching branches, creating worktrees, or merging branches. Preserve unrelated changes; keep the change focused. TDD, extra review skills and subagents are not mandatory unless requested or required.
3. Inspect the task diff and execute every applicable case with the least redundant evidence that actually establishes its conditions and expected results. Record the actual result, version and evidence using the shared workflow. Run other user- or repository-required checks; reuse only still-applicable results and rerun affected cases after changes.
4. Apply the mandatory [implementation status write-back](../test-case-workflow/references/implementation-status.md) before reporting or completion actions, including partial or blocked work. Declare the approved scope verified only when every applicable case passes with valid evidence and required write-backs succeed. Report failed, blocked, pending, unexecuted or stale cases and keep completion actions blocked. If the user explicitly approves a narrower scope, report exclusions and do not claim the original scope passed.

Leave changes in the working tree by default. Commit, push or open a PR only when requested, authorized and the applicable verification gate passes. Do not invoke fast-implement opaquely if that would bypass this gate.
