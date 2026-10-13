# Threat Model

## Scope

This is an initial design-level threat model for an enterprise IT support agent. It is not a completed security assessment or certification.

## Assets to protect

- Employee identity and authorization context
- Internal documents and restricted knowledge
- Tickets, configuration data, and enterprise-system records
- Credentials, tokens, and tool permissions
- Model prompts, outputs, and evaluation datasets
- Audit records and operational telemetry

## Threats and mitigations

| Threat | Example | Design mitigation | Validation evidence |
|---|---|---|---|
| Prompt injection | A retrieved page instructs the agent to reveal secrets | Treat retrieved text as untrusted data; isolate instructions; enforce policy outside the model | Adversarial retrieval tests |
| Cross-user data exposure | Search returns a document the caller cannot access | Apply authorization at retrieval time and verify permissions after retrieval | Access-control test matrix |
| Excessive tool privileges | Agent can close tickets or modify accounts unnecessarily | Narrow allowlisted tools and service identities | Permission review and negative tests |
| Unauthorized action | Model initiates a consequential change | Separate proposal from execution; require explicit approval | Tests proving no execution without approval |
| Sensitive data leakage | Prompts or logs contain secrets or personal data | Minimize data, redact logs, define retention and provider policy | Data-flow review and leakage tests |
| Hallucination | Unsupported troubleshooting instructions | Ground answers in sources; cite evidence; abstain when evidence is weak | Groundedness evaluation |
| Denial of service / cost abuse | Repeated long requests exhaust quota | Authentication, rate limits, token budgets, timeouts, quotas | Load and abuse tests |
| Supply-chain compromise | Dependency or container image is compromised | Pin and scan dependencies; review provenance; patch regularly | Dependency and image scan reports |
| Audit tampering | Action history is altered or incomplete | Restrict write access; protect retention; correlate approval and execution events | Audit integrity review |
| Model/provider outage | Responses time out | Timeouts, bounded retries, fallback policy, graceful degradation | Failure-injection tests |

## Mandatory design rules

- The model is not the authorization system.
- Tool calls must be validated and authorized by deterministic controls.
- Retrieved content must never be allowed to grant permissions.
- Secrets must not be committed to the repository.
- Human approval must be bound to a specific action, target, and expiry.
- Logs should capture what is needed for security and diagnosis, not raw sensitive content by default.

## Residual risks

Model behavior is probabilistic. Prompt injection defenses are not perfect, and source citations do not guarantee correctness. High-impact actions require independent controls, testing, monitoring, and accountable human ownership.

## Review checklist

- [ ] Data flows and trust boundaries documented
- [ ] Data classification and retention approved
- [ ] Identity and tool permissions reviewed
- [ ] Abuse cases and negative tests defined
- [ ] Approval and emergency-stop behavior tested
- [ ] Incident response owner assigned
- [ ] Security review completed before production
