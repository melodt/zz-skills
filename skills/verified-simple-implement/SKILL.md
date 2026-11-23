---
name: verified-simple-implement
description: Implement a bounded spec or ticket using simple-implement practices and documented test-case verification. Use when focused implementation must pass traceable functional cases before completion.
---

# Verified Simple Implement

Read the sibling [test-case-workflow](../test-case-workflow/SKILL.md) and [simple-implement](../simple-implement/SKILL.md). Install all three directories together. Apply the original skill's implementation, focused validation, and final review practices, while following the test-case workflow and gates below. User instructions and repository rules remain applicable.

1. Read the supplied spec or ticket and available detailed design. Before implementation, generate or update the feature's test cases and identify the task's applicable case IDs and prerequisites. If no spec, ticket, or detailed design is readable, report the missing source and stop formal case generation; do not claim case verification or perform completion actions. Continue authorized work that does not depend on the missing source.
2. Implement the requested behavior using simple-implement's bounded approach. Keep the cases and their source links current. If an expectation is unresolved, mark it 待确认 and continue independent work.
3. Review the final task diff and execute all applicable cases using the shared workflow. Record actual results, tested version, and evidence; reassess and rerun cases affected by subsequent changes. Run other checks required by the user or repository.
4. Only after all cases in the approved task scope pass with valid evidence may the task be declared verified or its authorized completion actions, including a commit, occur. Preserve failures, blockers, unexecuted and stale results and report incomplete verification. If the user explicitly approves a narrower scope, report excluded cases and do not claim the original scope passed.

Apply simple-implement's commit policy only after the gate and subject to user and repository instructions. Do not invoke the original skill as an opaque workflow that could commit before verification.
