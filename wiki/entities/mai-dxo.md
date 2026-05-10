---
type: entity
title: Microsoft AI Diagnostic Orchestrator (MAI-DxO)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [model-family/llm, model-family/foundation-model, task/diagnosis, organization/microsoft]
---

# Microsoft AI Diagnostic Orchestrator (MAI-DxO)

A **multi-agent AI system** developed at Microsoft for clinical diagnosis. Used in the AI Index 2026's most-cited diagnostic benchmark result.

## Headline result

The primary publication is *Sequential Diagnosis with Language Models*, Nori, Horvitz et al., ArXiv Jun 2025 (`arxiv.org/abs/2506.22405`), summarized in [ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) slide 45 and the AI Index 2026 Ch. 6.2 (p. 273).

| Setup | Accuracy | Cost |
|---|---|---|
| **MAI-DxO + o3 (no budget constraints)** | **80%** (slide 45) / **85.5%** (AI Index summary) | Up to 70% lower than off-the-shelf o3 |
| Off-the-shelf o3 | 78.6% | $7,850 / case |
| MAI-DxO + o3 (cost-optimized) | 79.9% | $2,397 / case |
| MAI-DxO + o3 (max accuracy) | 85.5% | $7,184 / case |
| 21 practicing physicians (5–20 years experience), unaided | **~20%** | — |

The ARISE summary uses the 80% number; the AI Index uses the 85.5% (max-accuracy) configuration. Both agree on the ~20% physician baseline.

## Architecture

Per the ARISE summary (slide 45) and the primary paper:
- **Multi-agent simulation of a virtual panel of five physicians.** A single LLM role-plays five distinct medical personas, each contributing specialized expertise.
- **Sequential decision problem.** Diagnosis is framed as iterative — the system decides which test to order *next* until reaching a confident diagnosis, rather than producing a one-shot differential.
- **Built on the Sequential Diagnosis Benchmark.** 304 NEJM clinicopathological-conference cases (2017–2025) converted from static cases into stepwise diagnostic encounters.
- **Model-agnostic.** MAI-DxO is compatible with any frontier model; ARISE shows accuracy gains across multiple base LLMs.

## Caveats

- Tested against **NEJM CPC cases** — diagnostically challenging cognitive evaluations, not real-world clinical workflow. See [clinical-validation](../concepts/clinical-validation.md).
- The 21 physicians worked **"under comparable conditions"** — i.e., without their usual tools (EHR, time, colleagues, references). The 85.5% vs. ~20% gap reflects a constrained comparison, not full-context-of-practice.
- More deployment-realistic benchmarks ([medagentbench](../concepts/medagentbench.md), 300 EHR-derived tasks) show the best AI agents top out at 70% (Claude 3.5 Sonnet) — strong on queries (85%), weak on actions (54%). The leap from "NEJM CPC accuracy" to "EHR action competence" is the unsolved gap.
- The **optimization paradox** finding (Bedi/Shah ArXiv Jun 2025) is a cautionary counterpoint: multi-agent systems with the *strongest* individual components can underperform less-optimized ones because of breakdowns in inter-agent information flow. MAI-DxO's success doesn't generalize automatically to other multi-agent designs.

## Why this result matters

MAI-DxO is the most prominent illustration in 2025–26 of a **multi-agent framework outperforming a single LLM** on clinical reasoning. Multi-agent gains over single-agent baselines ranged 7%–60% across published benchmarks (Gorenshtein et al., Zheng et al., Liu et al., 2025). MAI-DxO sits at the upper end and is accompanied by name-recognition (Microsoft + OpenAI) that makes it influential in policy and investment discussions.

It's also the most likely candidate for being **misinterpreted** — the case-bench-vs-clinical-practice distinction is exactly what the [arise-network](arise-network.md) *State of Clinical AI Report* warns about.

## Open questions

- Whether MAI-DxO has been or will be tested in prospective deployment.
- Whether Microsoft is pursuing an [fda-510k-pathway](../concepts/fda-510k-pathway.md) (or De Novo) authorization for any clinical use case.
- Performance on under-represented populations and rare diseases (NEJM CPC cases skew toward unusual presentations, but the demographic distribution of those cases is its own selection bias).
- How MAI-DxO performs on [noharm](../concepts/noharm.md) (severe-harm probability in real consult cases) — this is the safety axis NEJM CPC accuracy doesn't measure.

## Related
- [agentic-clinical-ai](../concepts/agentic-clinical-ai.md) — the broader category.
- [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md) — single-LLM baseline (o1-preview NEJM cases).
- [clinical-validation](../concepts/clinical-validation.md) — evidence-base context.
- [amie](amie.md) — Google's diagnostic-dialogue counterpart, with comparable-but-different evidence base.

## Sources
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (slide 45, primary citation)
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2, p. 272–273, summary)
