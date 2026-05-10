---
type: concept
title: MedHELM — Stanford physician-grounded clinical-workflow benchmark
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [evaluation/external-validation, task/clinical-workflow]
---

# MedHELM

A Stanford benchmark suite covering **35 distinct benchmarks** organized into a physician-validated taxonomy of **5 categories, 22 subcategories, 121 tasks** — designed to evaluate LLMs against real clinical workflow tasks rather than knowledge MCQ. **12 of the 35 benchmarks use real EHR data.** *Bedi, Shah et al., ArXiv Jun 2025.*

## Five categories

1. Administration and workflow
2. Clinical decision support
3. Clinical note generation
4. Medical research assistance
5. Patient communication and education

29 physicians built the taxonomy to ensure alignment with day-to-day clinical work — a direct response to the *Bedi/Shah JAMA Jan 2025* finding that prior LLM evaluations focused 95% on accuracy of medical-knowledge questions and almost ignored administration tasks.

## Headline 2025 results

Across 9 frontier models:

- **DeepSeek R1** (0.66) and **o3-mini** (0.64) led overall.
- **Claude 3.5 Sonnet** achieved comparable results at ~40% lower estimated computational cost.
- LLMs excel at **documentation (0.74–0.85) and patient communication (0.76–0.89)**.
- LLMs underperform on **clinical decision support (0.61–0.76)** and especially **administration & workflow (0.53–0.63)** — the very tasks clinicians most want automated.

## Why this is important

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) flags MedHELM as evidence that **the most-studied tasks (knowledge MCQ) are not the tasks that matter most for deployment**, and that frontier LLMs are *weakest* on the workflow tasks clinicians most want help with. This is the empirical bridge from Goh's prior critique ("we are over-measuring medical knowledge") to a path-forward benchmark.

Together with [healthbench](healthbench.md) and [medagentbench](medagentbench.md), MedHELM defines the 2025 generation of "clinical-workflow-realistic" evaluations — moving the field beyond MedQA saturation.

## Caveats

- Benchmark itself is a Stanford artifact; broader uptake by OpenAI/Anthropic/Google will determine influence.
- Real-EHR coverage (12/35 tasks) is partial — most benchmarks still use synthetic or curated data.
- Cost-per-task estimates depend on model APIs at a moment in time.
