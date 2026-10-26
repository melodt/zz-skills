---
name: simple-grill-with-docs
description: Stress-test a plan through focused questions and keep a Markdown decision document current. Use when the user asks to grill a plan and capture or update the decisions in a document.
---

Interview the user until the current goal, scope, and next step are clear. Map unresolved decisions as a **design tree**, bounded by the user's current goal. Expand a branch only when its answer could materially change that goal's scope, feasibility, or next step; leave speculative future needs outside the tree. Recommend the simplest option that meets stated requirements; add a mechanism only for a concrete requirement or evidenced failure.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask now without guessing at answers you haven't heard yet. Ask the most consequential frontier questions, normally up to three per round: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like so, using the user's language:

```
Q1 - **<question title>**: <question and meaningful options>

Recommendation: <your recommended answer and brief reason>
```

Each round the user answers reshapes the tree. Recompute the frontier using the same scope boundary. A question whose answer depends on another question still open in this round belongs to a later round. Revisit a settled decision only when new evidence or a changed requirement invalidates it.

Finding **facts** is your job, never the user's. Consult relevant existing docs and project evidence as needed. Ask the user for decisions that materially affect the goal, scope, consequential risks, or next step. For reversible details with little consequence, choose the simplest adequate default and label it as an assumption; reserve missing consequential decisions for the user.

Keep one Markdown document current: use the user's path, otherwise reuse the relevant existing plan, or create `docs/<topic>.md`. Start with what is already known before asking questions; after each answered round, update the document before asking more. Capture only the current goal and scope, agreed decisions with brief reasons, assumptions, unresolved blockers, and next step. Distinguish agreed decisions from recommendations and assumptions. Preserve unrelated content when editing an existing document; omit empty sections and scale detail to the task.

The session is done when no unresolved decision would materially change the current goal's scope, feasibility, or next step. Finalize the document and report its path and any remaining assumptions. A round is unnecessary if the available context already meets this condition. Writing the document is part of this skill; implement the plan only when the user requests implementation.
