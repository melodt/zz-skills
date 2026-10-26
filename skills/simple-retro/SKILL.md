---
name: simple-retro
description: Review a coding session for evidenced sources of rework or wasted effort and recommend minimal improvements. Use when the user requests a retrospective or asks how to make future agent runs more efficient.
---

Review the session the user specifies, defaulting to the current conversation. The outcome is a small set of useful improvements to future work, grounded in what actually happened.

## Find evidence

Start with the available conversation, tool results, and artifacts. Consult additional logs or configuration only to resolve a specific uncertainty relevant to a candidate finding. Keep retrieval scoped to the relevant session and files. If evidence is unavailable, state that limit rather than inferring events or measured savings.

Look for observed failures, repeated exploration, unnecessary confirmations, redundant tests, branch/worktree overhead, excessive tool output, or instructions that caused scope growth. These are prompts for investigation, not categories that must each produce a finding. Separate tool or environment limitations from agent choices and explicit user requirements.

## Choose the smallest effective correction

For each candidate, identify the demonstrated cause before proposing a fix. Prefer removing, clarifying, reusing, or repairing existing instructions and tools over adding a new workflow.

- For repeated navigation difficulty, propose a focused pointer or better use of existing discovery tools.
- For wasted validation, check which results were still valid and which edits actually required another run. Preserve checks required by the user, repository, or demonstrated risk.
- For an error a check could catch, inspect the relevant existing command or configuration first. Repair a broken or unused check when appropriate. Propose a new deterministic check when likely recurrence or impact justifies its execution and maintenance cost; absence of a hook or CI job alone is insufficient.
- For instruction problems, locate the conflicting, vague, redundant, or overly demanding rule. Prefer one correction at its source. A task-specific incident does not automatically justify a global rule.

Evaluate implementation and review as they occurred; follow the repository's actual standards and workflow. Keep access or tooling proposals scoped to the demonstrated information gap.

## Report and stop

Prioritize by demonstrated impact, recurrence, and expected benefit relative to maintenance cost. Normally report the strongest one to three findings, rather than filling a quota. For each, give:

- **Evidence and impact:** a concrete event or artifact and the resulting error, delay, or rework. Distinguish measured impact from estimates.
- **Minimal change:** the specific instruction, configuration, or tool behavior to adjust and why it addresses the cause.
- **Tradeoff and verification:** ongoing cost and how a future comparable task would show whether the change helped. Include uncertainty when the cause is not established.

It is valid to find no change worth making. Default to recommendations in chat. If the user also requested implementation, apply the supported changes within that scope, validate the affected artifacts, and report what changed and what remains unproven. Reuse an existing relevant document when persistence is requested; create a new document only when needed.
