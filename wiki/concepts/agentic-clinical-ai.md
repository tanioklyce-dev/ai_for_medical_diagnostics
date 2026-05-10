---
type: concept
title: Agentic clinical AI
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [task/diagnosis, model-family/llm, evaluation/benchmark, deployment]
---

# Agentic clinical AI

Autonomous and semi-autonomous AI agents that **reason across multiple steps, access external tools and data sources, and coordinate with other agents or human clinicians** to complete complex clinical tasks. A major emerging category in 2025–2026 — distinct from a single LLM answering a one-shot prompt.

## Why the category emerged in 2025

Conventional AI models generate predictions or classifications **in isolation**. Agentic systems take in additional context (EHR records, lab results, imaging) and operate over multiple steps — order tests, integrate results, adjust the differential, generate a recommendation. The 2025 scoping review identified **43 studies** evaluating agentic AI in healthcare, with **84% (36/43) published in 2025 alone** — i.e., it's a brand-new literature.

## Headline results

### [mai-dxo](../entities/mai-dxo.md) + OpenAI o3 on NEJM cases
- **85.5%** accuracy on diagnostically challenging cases drawn from the New England Journal of Medicine.
- **~20%** for 21 practicing physicians with 5–20 years of clinical experience working under comparable conditions (no AI tools).

This is the signature 2025 result for clinical agentic AI — see [mai-dxo](../entities/mai-dxo.md) for full detail.

### Multi-agent gains over single-agent baselines
Across published benchmarks, multi-agent frameworks showed gains of **7% to over 60%** in diagnostic accuracy vs. single-agent baselines (Gorenshtein et al., Zheng et al., Liu et al., 2025). The mechanism: assigning specialized roles (diagnostician, pharmacist, etc.) and coordinating through structured reasoning protocols.

### MedAgentBench (Jiang et al., 2025)
A more deployment-realistic benchmark:
- **300 clinically derived tasks** in a virtual EHR environment.
- Best-performing model achieved **69.7% task success rate**.
- The conclusion in the AI Index: "despite access to advanced capabilities such as tool use and iterative reasoning, the evidence base for reliable autonomous clinical AI agents remains early-stage."

The gap between **NEJM-style case benchmarks (85%+)** and **EHR-task benchmarks (~70%)** is informative — capabilities degrade as the environment gets messier.

## Adjacent: agentic AI for biomedical *discovery* (vs. clinical care)

The Medicine chapter highlights several research-side biomedical agents that aren't directly clinical but inform the trajectory:

- **Robin** — automated discovery framework; linked literature-based hypothesis generation with experimental data analysis; identified the ROCK inhibitor **ripasudil** as a novel candidate for dry age-related macular degeneration.
- **STELLA** — autonomous bioinformatics agent; expanded its own tool capabilities.
- **Biomni** (Stanford) — general-purpose biomedical agent across **25 subfields**, integrating 150 specialized tools, 105 software packages, 59 databases.
- **Agent Laboratory** (AMD / Johns Hopkins) — assigns PhD, Postdoc, and ML Engineer roles to agents within a simulated lab structure.
- **The Virtual Lab** — LLM Principal Investigator orchestrating specialist scientist agents; produced **92 novel nanobody binder designs for SARS-CoV-2** (require experimental validation).

These systems are early-stage but represent a coordination pattern that may eventually translate back into clinical workflows.

## What's still missing

- **Real-world deployments** — almost all evidence so far is benchmark-based.
- **Liability** — who's accountable when a multi-agent system produces a harmful recommendation through a chain of decisions?
- **Calibration and uncertainty propagation** — errors compound across multi-step reasoning.
- **Workflow integration** — agentic systems need EHR access, ordering, and oversight loops that vary across institutions.

The Responsible AI chapter notes (Ch. 3.3) that across surveyed organizations, **security and risk concerns (62%) are the top barrier to scaling agentic AI**, ahead of technical limitations (38%) and regulatory uncertainty (38%).

## Related
- [mai-dxo](../entities/mai-dxo.md) — flagship clinical agentic system.
- [llm-clinical-reasoning](llm-clinical-reasoning.md) — single-LLM reasoning baseline.
- [clinical-validation](clinical-validation.md) — the evidence-rigor context.
- [ai-hallucination-medical](ai-hallucination-medical.md) — failure modes that compound across multi-step reasoning.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2 highlight box on AI Agents in Clinical Medicine, p. 272–273; Ch. 6.1 highlight on Automated and Agentic Biomedical Discovery, p. 268; Ch. 3.3 on agentic AI scaling barriers, p. 145)
