---
name: verified-implement
description: Implement one spec, ticket, or bounded feature using traceable test cases and a verified completion gate. Use when the user requests single-task implementation with documented test-case verification.
---

# Verified Implement

Read [test-case-workflow](../test-case-workflow/SKILL.md) and apply its preparation, evidence, status, and completion rules throughout. The two skill directories must be installed together as siblings. Read the requested spec or ticket, available detailed design, and applicable project instructions; establish the task scope and resolve consequential conflicts before implementing the affected behavior.

1. Before implementation, generate or update the feature case document using the shared workflow. Identify the task's case IDs and prerequisites. Continue work independent of unresolved cases, but retain their 待确认 or 阻塞 status.
2. Locate and read the installed third-party `implement` skill and relevant referenced guidance. Use its applicable implementation and TDD practices, including its testing-seam confirmation when required, subject to the user's instructions, repository rules, and authorization. Recheck the installed version each run; do not modify it. If unavailable, report that integration gap and implement the authorized task using the available project workflow and the test-case gate.
3. Keep the third-party skill's commit or other completion actions under this entry's control: do not invoke it as an opaque workflow if it could perform them before the gate. Instead follow its compatible steps in sequence and defer those actions. If the flows cannot be reconciled, pause the affected action and report the conflict.
4. Implement the task incrementally, keeping cases and source links current. Perform required code review and checks, then execute every applicable case against the final relevant version using the shared workflow. If review or subsequent changes affect evidence, reassess and rerun as required.
5. Only once all cases in the approved task scope pass with evidence may the task be called verified and its authorized completion actions occur. If any case is unconfirmed, unexecuted, failed, blocked, or needs rerun, preserve results, do not perform affected completion actions, and report the task as not fully verified. For a user-approved narrower scope, report all exclusions and do not claim the original scope passed.

This entry does not itself authorize a commit, external publication, or issue closure. Follow explicit user and repository instructions for these actions.
