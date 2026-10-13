# Cost and TCO Framework

## Purpose

Compare architecture options using workload-specific measurements. This document defines a method; it does not claim measured savings or current vendor prices.

## Define the workload

Record these inputs before comparing providers:

- Requests per month
- Input and output tokens per request (median and p95)
- Retrieval calls and reranking usage
- Model calls per workflow
- Embedding and indexing volume
- Storage and retention requirements
- Availability, latency, and data-residency requirements
- Engineering, security, and operations effort

## Cost categories

| Category | Examples |
|---|---|
| Model inference | Input/output tokens, provisioned capacity, local hardware utilization |
| Retrieval and data | Embeddings, vector index, object storage, ingestion |
| Application runtime | Containers, compute, networking, API gateway |
| Observability | Traces, metrics, logs, retention |
| Security | Identity, key management, scanning, audit storage |
| Human operations | Review, escalations, evaluation, incident response |
| Delivery | Engineering, testing, upgrades, support |

## Formulas

**Monthly TCO** = inference + retrieval/data + application/runtime + observability + security + operations + amortized delivery costs.

**Cost per successful resolution** = total monthly TCO / number of successfully resolved requests in that month.

**Human review rate** = requests requiring human review / total requests.

Include unsuccessful requests and human review costs; do not compare only the price of model tokens.

## Comparison method

Evaluate at least three options:

1. Managed model and managed retrieval
2. Managed model and self-managed retrieval
3. Local model and local retrieval

A hybrid option can be added if routing low-risk or simple requests to a smaller model is justified by evaluation results.

For each option, record quality, p50/p95 latency, availability, operational hours, data constraints, portability, and monthly TCO at low, expected, and peak demand.

## Decision rules

- Reject an option that fails security, quality, or latency requirements, even if it is cheaper.
- Include engineering and on-call effort in TCO.
- Test actual representative requests; do not rely on vendor claims alone.
- State assumptions, measurement dates, currency, and exclusions.
- Re-evaluate when model prices, traffic, or requirements materially change.

## Results table template

| Option | Quality pass rate | p95 latency | Monthly TCO | Cost/success | Operational burden | Decision |
|---|---:|---:|---:|---:|---|---|
| Managed + managed retrieval | TBD | TBD | TBD | TBD | TBD | Not evaluated |
| Managed + self-managed retrieval | TBD | TBD | TBD | TBD | TBD | Not evaluated |
| Local + local retrieval | TBD | TBD | TBD | TBD | TBD | Not evaluated |

TBD values must remain blank or explicitly marked pending until measured.
