# Evaluation Plan

## Goal

Determine whether the system is useful, grounded, safe, and economically viable for the defined IT support workflow.

## Evaluation dataset

Create a versioned, permission-reviewed dataset containing:

- Common questions answerable from approved sources
- Questions with conflicting or outdated documentation
- Questions with insufficient evidence
- Cross-access attempts against restricted documents
- Prompt-injection attempts in user messages and retrieved content
- Requests for actions that require approval
- Out-of-scope requests and ambiguous questions

Use synthetic or approved sanitized data in the public repository. Do not publish customer or employer data.

## Metrics

| Dimension | Example metric | Interpretation |
|---|---|---|
| Answer quality | Human-rated correctness | Is the answer correct for the task? |
| Grounding | Claims supported by cited sources | Does evidence support the response? |
| Retrieval | Recall@k on labeled queries | Were relevant authorized documents found? |
| Safety | Policy violation rate | Did the system cross a defined safety boundary? |
| Authorization | Unauthorized retrieval/action count | Must be zero in the test suite |
| Reliability | Successful completion rate | Did the workflow complete correctly? |
| Performance | p50/p95 latency | Is response time acceptable? |
| Economics | Cost per successful resolution | Is the solution viable? |
| Human factors | Escalation and re-open rates | Does it reduce work without hiding failures? |

## Release gates

Agree numerical thresholds with business, security, and operations owners before testing. Block release on any confirmed unauthorized action, cross-user data exposure, or critical policy violation.

For quality metrics, inspect both aggregate performance and failure categories. A good average must not conceal severe failures in high-risk scenarios.

## Test protocol

1. Freeze the dataset and record its version.
2. Record model, prompt, retrieval, and configuration versions.
3. Run the same cases across candidate options.
4. Separate automated scoring from human review.
5. Review failures and disagreements.
6. Repeat after meaningful changes.
7. Publish methods, sample sizes, limitations, and results.

## Reporting template

- Dataset version:
- Test date:
- Model/provider and version:
- Retrieval configuration:
- Number of cases:
- Correctness:
- Groundedness:
- Critical safety failures:
- Unauthorized retrieval/actions:
- p50/p95 latency:
- Cost per successful resolution:
- Known limitations:
- Reviewer and decision:

No result should be reported until the test has actually been run.
