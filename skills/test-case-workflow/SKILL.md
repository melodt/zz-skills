---
name: test-case-workflow
description: Generate, maintain, and execute traceable functional test cases from specs, tickets, and detailed designs. Use for test-case generation or verification against a documented feature; distinguish drafting cases from executing them.
---

# Test Case Workflow

Generate or update cases when asked to prepare tests; execute existing cases when asked to verify; do both when the user requests both. Generating cases does not authorize implementation or execution. Verification does not authorize production changes, commits, publishing, or closing work.

## Prepare cases

1. Read all explicitly supplied sources and relevant available spec, tickets, and detailed design. Identify each source and version or stable location, the requested feature and ticket scope, missing sources, and inaccessible explicitly requested materials. At least one of these three source types must be readable to produce formal cases; otherwise report the missing input and stop case generation.
2. Build a coverage map from each in-scope behavior, role, operation, rule, state, and acceptance criterion to case IDs or an explicit unresolved or inapplicable reason. Map cases to applicable tickets, including cross-ticket interactions. If sources conflict, identify both claims and their consequences; mark affected expectations 待确认 and continue independent work. Do not invent business limits, error messages, or expected behavior.
3. Choose applicable normal, boundary, error, permission, state, and integration scenarios from the evidence and risk. Priority orders execution; it does not remove any in-scope case from the completion gate. For the case schema and document structure read [the template](references/test-case-template.md).
4. Maintain one Markdown document per feature. Use the user's chosen path or the project's established convention, otherwise `docs/<feature>-test-cases.md`. Update an existing document without overwriting unrelated material or others' changes. Assign stable, feature-unique case IDs; retain IDs and execution history for unchanged cases. Record merges, removals, changed sources, and affected prior results; avoid duplicates. Mark changed or otherwise invalidated results 需复验.
5. Report the document, read and missing sources, coverage gaps, conflicts, and status. A case document alone is not verification; initial execution fields are empty and state is 未执行 or 待确认.

## Execute and assess

1. Identify the original scope and all applicable case IDs, including necessary interactions; record the scope and the tested revision or other identifiable version. Only the user may explicitly approve a narrower scope. Record the approval and excluded cases, and report those exclusions separately.
2. Use authorized environments and data. Execute each applicable case with its prerequisites, data, steps, and observable expected results. An automated test counts only where its actual coverage proves the case's relevant conditions and expectations; otherwise perform the missing checks or report them unverified. Never record credentials or tokens in the document.
3. For each case record actual outcome, status, execution time, executor or tool, tested version, and accessible evidence identifying the case and result. Retain failed and blocked attempts and their resolution or reruns. Use 通过 only for an actual matching result backed by valid evidence; use 失败 for an observed mismatch, 阻塞 for missing environment, dependency, permission, or execution access, and 待确认 for unresolved expectations. An unrun case stays 未执行.
4. Reassess earlier passing evidence when code, requirements, environment, data, or dependencies change. Reuse it only when it remains applicable to the current version and conditions; otherwise mark 需复验 and rerun affected cases. Expand verification when the impact cannot be bounded. Preserve evidence and reconcile concurrent changes without silently overwriting them.
5. Report tested scope, version, case IDs and statuses, evidence, failures, blockers, missing coverage, excluded cases, and next action. Declare the approved scope verified only when every applicable case is 通过 with valid evidence. 待确认、未执行、失败、阻塞 and 需复验 are not passing. A narrowed scope never represents the original full scope as passed.

If a document cannot be written or a needed environment or permission is missing, preserve what can be recorded and report the failure; do not claim completion. Apply the user's authorization and higher-priority instructions to every action.
