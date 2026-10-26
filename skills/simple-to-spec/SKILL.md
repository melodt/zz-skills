---
name: simple-to-spec
description: Turn an existing conversation or plan into a concise, implementable spec. Use when the user wants agreed requirements captured without another interview or extensive speculative user stories.
---

Synthesize the conversation, supplied documents, and existing codebase understanding into a spec. Preserve the user's scope and agreed decisions. Reuse known context; investigate only unknown facts that could materially change the spec. Use relevant project terminology and respect applicable repository instructions and architectural decisions.

Write a useful draft directly. Label assumptions, recommendations, and unresolved decisions separately from agreed requirements. Ask only when an ambiguity prevents a useful draft; routine confirmation of the document or test boundaries is unnecessary. Missing consequential decisions remain explicit blockers, not invented answers.

## Spec

Keep the document proportional to the change. Capture:

- **Problem and scope:** the user's problem, intended outcome, and relevant exclusions.
- **Solution and decisions:** the simplest adequate behavior, necessary contracts or constraints, and implementation decisions already agreed or supported by evidence.
- **Acceptance criteria:** observable outcomes covering the requested behavior and material failure cases. Use user stories only when they clarify distinct needs; completeness means covering the agreed scope.
- **Validation:** the least costly reliable checks for those outcomes, reusing existing test boundaries and coverage where appropriate. Include user- and repository-required checks. Select test boundaries for useful behavioral evidence, rather than aiming for one highest-level test.
- **Assumptions and open questions:** only what remains relevant, with the effect of any blocker on implementation readiness.

Merge short sections and omit empty ones. Include verified code pointers or small contract examples when they materially aid implementation; distinguish existing behavior from proposed changes. Describe necessary validation without running tests or implementing the feature just to write the spec.

## Save and finish

Use the user's output path; otherwise update the relevant existing spec or create `docs/<topic>.md`. Preserve unrelated content when updating. If the user requests an in-chat draft, deliver it there.

Local output needs no issue-tracker setup. Publish externally only as part of the user's requested workflow, using the configured tracker conventions. Apply a readiness label only when unresolved decisions do not block implementation; report a failed publication without claiming success.

Check the document once for scope drift, unsupported claims, missing acceptance criteria, and unresolved blockers. Report its path or published reference and any blockers. Stop at the spec unless the user also requests tickets or implementation.
