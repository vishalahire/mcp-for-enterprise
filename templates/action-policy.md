# Governed action policy

Status — proposed template. This record describes a business control to implement and verify.

| Field | Policy entry |
| --- | --- |
| Action name, version and owner | |
| Business purpose and permitted use | |
| Target system and environments | |
| Requester roles and scope | |
| Eligible records and allowed fields | |
| Bounds on volume, value and time | |
| Data sensitivity and external effects | |
| Reversibility and correction procedure | |
| Requester confirmation rule | |
| Independent approver roles and separation of duties | |
| Conditions that require additional review | |
| Prohibited conditions | |
| Authoritative preview fields | |
| Approval lifetime and revocation rules | |
| Argument and record-version binding | |
| Execution identity and downstream authorization | |
| Atomic checks and concurrency control | |
| Idempotency and uncertain-outcome reconciliation | |
| Partial-failure and compensation behavior | |
| Audit fields and retention | |
| Policy version and approval reference | |
| Material change triggers | |

## Verification scenarios

Record expected and observed outcomes for allowed execution, denial, incorrect approver, changed arguments, wrong environment, changed record state, expired or revoked approval, duplicate execution, partial failure, uncertain outcome and direct-route bypass.

## Operating measures

Track approval waiting time, correction or rejection rate, stale proposals, execution failures, duplicate prevention and unauthorized execution attempts. Assign an owner to investigate exceptions.
