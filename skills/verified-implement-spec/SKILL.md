---
name: verified-implement-spec
description: Implement a complete spec and its dependent tickets with traceable per-ticket and integrated test-case verification. Use when delivering an entire spec with a documented completion gate.
---

# Verified Implement Spec

Read [test-case-workflow](../test-case-workflow/SKILL.md) and apply its preparation, evidence, status, and completion rules throughout. The two skill directories must be installed together as siblings. Read the spec, all associated tickets and dependencies, available detailed design, and applicable project instructions.

1. Before implementation, create or update one feature case document mapping behavior and cases to tickets and cross-ticket interactions. Record missing sources and decisions. Provide the source, case document, relevant case IDs, and scope to every implementer.
2. Locate and read the installed third-party `implement-spec` skill and its relevant referenced guidance. Recheck its current version each run and follow its applicable ticket, dependency, integration, TDD, and review practices, subject to user instructions, repository rules, and authorization. Do not modify it. If unavailable, report that integration gap and use the available project workflow while retaining the gates below.
3. Do not invoke the third-party workflow as an opaque operation when it might commit, close tickets, or mark a PR ready before verification. Coordinate compatible steps explicitly and defer completion actions until the applicable gate passes. If its required sequencing cannot be reconciled with that gate, pause the affected action and report the conflict. Use branches, subagents, worktrees, and external systems only when authorized and available.
4. Implement ready tickets in dependency order. Before each ticket's completion action, execute every applicable ticket case against its relevant version and record evidence. Unresolved or blocked cases prevent that ticket's completion action; preserve the results and continue independent work when possible.
5. After integration and required review, execute cross-ticket and integration-affected cases against the integrated version. Reassess and rerun any evidence invalidated by merges, review fixes, or other changes. Only declare the full spec verified and perform its authorized final completion actions when all applicable feature and integration cases have valid passing evidence.
6. Report per-ticket and integrated scope, case outcomes and evidence, blockers, and exclusions. A user-approved narrower verification scope can pass on its own terms, but never represents the original spec as fully verified. Preserve failed, unexecuted, blocked, pending, and stale cases as non-passing.

This entry does not itself authorize commits, PR changes, issue closure, or access to external systems.
