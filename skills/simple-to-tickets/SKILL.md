---
name: simple-to-tickets
description: Turn a spec, plan, or conversation into a small set of actionable tickets with acceptance criteria and genuine dependencies. Use when the user wants implementation tasks without excessive fragmentation or mandatory tracker setup.
---

Read the supplied spec or plan, including relevant updates when the source is an issue. Reuse the conversation and existing codebase understanding. Investigate only unknown facts that could materially change the task breakdown; respect applicable repository instructions and architectural decisions.

## Split only where useful

Choose the fewest tickets that remain understandable, actionable, and verifiable. A small spec can be one ticket. Split for independently deliverable outcomes, genuine prerequisites, or work too large to implement coherently. Prefer complete behavior slices through the layers actually involved; a local API, UI, or infrastructure change needs only its relevant layers.

Keep tightly coupled changes together. Add preparatory refactoring only when the current structure demonstrably obstructs the requested work. Use expand-contract when rollout compatibility requires old and new forms to coexist; otherwise prefer a coherent atomic change where feasible.

Record a blocking edge only when a ticket genuinely needs another ticket's result before it can start. Shared files or a preferred execution order alone are not dependencies. Keep the graph acyclic and list blockers before dependent tickets. A ticket boundary does not require a separate branch, worktree, commit, or full test run.

## Write the tickets

Produce an actionable draft directly, revising it when the user gives feedback. Ask only about unresolved choices that would materially change the breakdown. For each ticket, include:

- A stable local ID and short title.
- The outcome to deliver and necessary scope or contract details.
- Observable acceptance criteria traceable to the source spec.
- Genuine blockers by ID, or "None"; identify any unresolved external decision separately.

Reference shared spec decisions and validation guidance rather than duplicating them in every ticket. Add ticket-specific validation only when it addresses a distinct risk. Verified code pointers are useful when they clarify the work; a speculative file-by-file implementation plan is unnecessary.

Check once that every in-scope acceptance criterion is covered, the tickets introduce no extra requirements, dependencies are consistent, and material unknowns are explicit. A drafted ticket is planned work, not implemented or verified work.

## Save and finish

Use the user's output path; otherwise update the relevant existing task list or write one `docs/<topic>-tickets.md` containing all tickets and a reference to the source spec. Preserve existing ticket IDs, completion state, and unrelated content. Use separate local files when requested or required by the repository. If the user wants an in-chat breakdown, deliver it there.

Local output needs no issue-tracker setup. For requested external publication, use the configured tracker conventions, create tickets in dependency order, and map local blocker IDs to published identifiers or native blocking links. Publish only tickets whose scope is sufficiently settled, report any remaining blockers, and leave the parent issue unchanged unless the user requested a parent update. Report partial publication accurately so a retry can reuse existing issues.

Report the document path or published references, ticket count, and unresolved blockers. Stop at the breakdown unless implementation is also requested.
