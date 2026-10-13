# ADR-001: Use Bounded Agent Autonomy

- **Status:** Accepted as a reference-design decision
- **Context:** Enterprise agents may produce incorrect outputs or misunderstand untrusted instructions. Unrestricted tool execution can create material business risk.
- **Decision:** Separate read-only reasoning from consequential execution. Expose narrowly scoped tools through a policy-enforcing gateway. Require explicit human approval for sensitive or irreversible actions.
- **Alternatives considered:**
  - Unrestricted autonomous tool access: rejected because the blast radius is too large.
  - Human approval for every operation: safer but may add unnecessary friction for low-risk read-only tasks.
  - Fully deterministic workflow without an LLM: appropriate for some cases, but less flexible for natural-language understanding.
- **Consequences:** More explicit workflow states and approval handling; reduced autonomy by design; improved auditability and clearer accountability.
- **Validation:** Negative tests must demonstrate that unauthorized or unapproved actions cannot execute.
