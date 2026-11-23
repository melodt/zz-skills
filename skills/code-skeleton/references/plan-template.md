# Implementation Plan

## Metadata

| Field | Value |
|---|---|
| run_id | `{{run_id}}` |
| mode | `{{mode}}` |
| skill_version | `{{skill_version}}` |
| generated_at | `{{generated_at}}` |

## Inputs

| Source | Path | Version / hash | Role |
|---|---|---|---|
| spec | `{{path}}` | `{{hash}}` | `{{role}}` |

## Dependency order

1. `{{ticket_id}}` — `{{reason}}`

## Traceability matrix

| Source / design / acceptance ID | Ticket | Case ID / expected result | Module / interface / files | Skeleton / test placeholder | Verification / evidence | Status / gap |
|---|---|---|---|---|---|---|
| `{{source}}` | `{{ticket_id}}` | `{{case_and_expected}}` | `{{target}}` | `{{placeholder}}` | `{{verification}}` | `{{status_or_gap}}` |

Enumerate each in-scope design item and applicable case, including unmatched items and cross-ticket scenarios. Record input document versions, excluded scope, unresolved conflicts and the reason for any inapplicable item.

## File operations

| Ticket | Operation | Path | Reason | Conflict / risk |
|---|---|---|---|---|
| `{{ticket_id}}` | create / patch / skip | `{{path}}` | `{{reason}}` | `{{risk}}` |

## Open decisions and blockers

- `{{ticket_id}}`: `{{decision_or_blocker}}` — impact: `{{impact}}` — owner: `{{owner}}`

## Verification commands

| Layer | Command | Source | Timeout | Expected evidence |
|---|---|---|---|---|
| syntax | `{{command}}` | `{{source}}` | `{{timeout}}` | `{{evidence}}` |
