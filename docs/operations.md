# Operations and Observability

## Service objectives

Define service-level objectives with stakeholders before production. Candidate service indicators include successful workflow completion, p95 latency, error rate, escalation rate, cost per successful resolution, and critical policy violations.

## Events and telemetry

Capture, where appropriate:

- Correlation ID and workflow version
- Model/provider and configuration version
- Retrieval source identifiers and authorization outcome
- Tool name, validation outcome, and approval reference
- Latency by workflow stage
- Token usage or equivalent metering
- Error category, retry count, and final disposition
- Evaluation outcome and user feedback

Avoid storing full prompts, outputs, or retrieved documents by default. Apply redaction, access controls, retention limits, and data classification to telemetry.

## Operational controls

- Timeouts and bounded retries
- Rate and concurrency limits
- Token and spend budgets
- Circuit breakers or graceful degradation for unavailable dependencies
- Dead-letter or review paths for failed workflows
- Versioned prompts, tools, policies, and evaluation datasets
- Rollback procedures and change approval
- On-call ownership and incident escalation

## Human approval

An approval record should identify the requester, proposed action, target, relevant parameters, approver, timestamp, expiry, and execution result. Any change to the approved action invalidates the approval.

## Incident response

1. Stop or restrict the affected workflow when needed.
2. Preserve relevant audit evidence with privacy safeguards.
3. Determine scope, affected identities, tools, and data.
4. Revoke or reduce credentials if compromise is suspected.
5. Notify designated security and business owners.
6. Recover only after validating the fix.
7. Add regression cases and document lessons learned.

## Operational readiness checklist

- [ ] Dashboards and alerts reviewed
- [ ] Spend limits and rate limits configured
- [ ] Runbook and rollback tested
- [ ] Human escalation owner assigned
- [ ] Logs reviewed for sensitive data exposure
- [ ] Evaluation release gates enforced
- [ ] Backup and retention policies approved
- [ ] Security and operational sign-off completed
