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

| Source entry | Ticket | Module | Files | Verification | Status |
|---|---|---|---|---|---|
| `{{source}}` | `{{ticket_id}}` | `{{module}}` | `{{files}}` | `{{verification}}` | `{{status}}` |

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
