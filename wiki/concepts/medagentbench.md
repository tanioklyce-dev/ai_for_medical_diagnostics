---
type: concept
title: MedAgentBench — agentic clinical AI in a virtual FHIR EHR
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [evaluation/external-validation, task/clinical-workflow, model-family/llm]
---

# MedAgentBench

A Stanford benchmark designed to evaluate whether LLMs can function as **agentic teammates** inside a clinical EHR environment — not just answer questions, but read records, place orders, modify charts, and complete multi-step workflows. *Jiang, Chen et al., NEJM AI Aug 2025.*

## Construction

- Two physicians generated **300 commonly encountered clinical tasks**, half **query-based** (retrieve information from the chart) and half **action-based** (modify the chart — placing orders, updating documentation).
- Tasks operate in a **FHIR-compliant virtual EHR** with **100 patients** and **>700,000 data elements**.
- **pass@1** metric: success on a single attempt, evaluated across 12 frontier models.

## Headline results

- **Claude 3.5 Sonnet (70%)**, GPT-4o (64%), DeepSeek-V3 (63%) led overall.
- Strong on queries (**Claude 3.5 Sonnet 85%**), weak on actions (**Claude 3.5 Sonnet 54%**).
- The query-action gap is the central finding: LLMs that perform well at retrieval struggle with multi-step planning, EHR-state mutation, and workflow reliability.

## Why ARISE highlights it

Physicians spend ~73% of their time on indirect care (admin / EHR / coordination) — exactly the tasks where current LLMs are weakest, per [medhelm](medhelm.md). MedAgentBench measures the *next* layer: not just whether a model can synthesize a workflow plan, but whether it can *execute* against a structured EHR. [ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) treats it as a **next-generation benchmark** for agentic clinical AI, complementary to [healthbench](healthbench.md) (conversational) and [medhelm](medhelm.md) (clinician-task evaluations).

## Implications

If the action-execution gap is the bottleneck (and ARISE argues it is), then near-term clinical-AI deployments should:

- Limit agents to query-shaped workflows where current LLMs are reliable.
- Wrap action workflows in human-in-the-loop confirmation steps.
- Treat agent-action benchmarks as a deployment readiness gate, not just a research target.

This connects to the [agentic-clinical-ai](agentic-clinical-ai.md) optimization paradox finding (Bedi/Shah ArXiv Jun 2025): even when individual agents are strong, end-to-end agentic systems can perform worse than less-optimized ones because of breakdowns in information flow.

## Caveats

- Virtual EHR — generalization to specific commercial EHR vendors (Epic, Cerner) will require system-specific evaluation.
- 100 patients × 300 tasks is a research-scale benchmark, not a deployment-scale one.
- pass@1 is harsh; real workflows allow multiple attempts and human review. Real-world action-success rates would likely be higher with retries.
