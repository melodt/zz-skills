# Functional test case document

Adapt the headings to project conventions while retaining the fields and traceability below. Do not copy illustrative data into real cases as fact.

## Sources and scope

- Feature and original scope; approved current scope and explicitly excluded cases, if any.
- Each source with location/version, missing or inaccessible sources, and relevant ticket dependencies.
- Conflicts and unresolved questions, their impact, and the decision or source needed to resolve them.

## Coverage

For each in-scope behavior, role, operation, rule, state, and acceptance criterion, record source location, applicable ticket, case IDs, and uncovered / pending / inapplicable explanation. Identify cross-ticket cases.

## Cases

Use a stable feature-unique ID such as `TC-<FEATURE>-001` and retain it across updates. For every case record:

- Module, title, priority, type, source location and applicable ticket IDs.
- Prerequisites, environment, test data, ordered actionable steps, and independently observable expected results. Mark unknown business values or expectations 待确认 rather than guessing.
- Current status: 待确认 / 未执行 / 通过 / 失败 / 阻塞 / 需复验.
- Actual results, execution time, executor or tool, tested version, and accessible evidence identifying the case and outcome; leave empty until executed.
- History of failed or blocked attempts, resolutions, reruns, and changes affecting IDs or evidence. Preserve relevant prior records.

## Summary

List status counts and case IDs, actual verified scope and version, exclusions, unresolved coverage, failures, blockers, and the resulting completion judgment. Never label an unexecuted case or an entire feature as passed based only on generation.
