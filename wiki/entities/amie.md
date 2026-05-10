---
type: entity
title: AMIE — Articulate Medical Intelligence Explorer (Google)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [model-family/multimodal, model-family/llm, task/diagnosis, task/management, evaluation/external-validation]
---

# AMIE (Google's Articulate Medical Intelligence Explorer)

A Google DeepMind / Google Research conversational diagnostic AI built on Gemini. Across 2025, AMIE accumulated the strongest published evidence base for **LLM-based clinical reasoning under realistic dialogue conditions** — specifically, multi-turn history-taking, multi-visit longitudinal management, and multimodal interpretation. It is a recurring reference point in the ARISE [State of Clinical AI 2026](../sources/arise-state-of-clinical-ai-2026.md), appearing in both Model Performance and Patient-Facing AI sections.

## What it is

A two-part agentic system: a fast **Dialogue Agent** captures relevant history-of-present-illness, while a slower **Management Reasoning Agent** uses long-context reasoning grounded in clinical guidelines (NICE, BMJ Best Practice). For multimodal cases AMIE adds a state-aware framework that requests, interprets, and integrates skin photos, ECGs, and clinical documents during the conversation. Patient profiles for evaluation are richly synthesized using Gemini 2.0 Flash plus public datasets.

## Headline 2025 results

- **Diagnostic dialogue (n=159 simulated cases, 20 physicians)**: AMIE matched or exceeded primary care physicians on 30/32 specialist axes and 25/26 patient-actor axes — accuracy, communication quality, empathy. *Tu, Natarajan et al., Nature Apr 2025.*
- **Multi-visit primary care (100 three-visit scenarios across cardiology, pulmonology, neurology, OBGYN/urology, GI)**: non-inferior to 21 PCPs across guideline-based decisions, treatment planning, longitudinal care; produced more guideline-precise plans; outperformed PCPs on harder medication-reasoning RxQA questions. *Palepu, Schaekermann et al., ArXiv Mar 2025.*
- **Multimodal OSCE (105 scenarios)**: outperformed PCPs on top-1 through top-10 differential diagnostic accuracy, integrating skin photos, ECGs, documents into a structured state-aware dialogue. *Saab, Freyberg, Tanno et al., ArXiv May 2025.*

## Caveats

- All evaluations to date are **simulated patient interactions**, not real-patient care. The 2025 results sit firmly on the *capability-ahead-of-evidence* side of the [clinical-validation](../concepts/clinical-validation.md) split — there is no prospective deployment evidence yet.
- The text-chat interface differs from typical clinical practice; integration into actual workflow has not been studied.
- Results are reported by Google's own teams; the broader independent replication base is thin.

## Position in the field

AMIE is the dominant data point for "single AI system can hold its own against PCPs across diagnosis, management, and multimodal interpretation." It is a key example used to argue AI diagnostic capability *exists*; it is not yet evidence that AI improves *patient outcomes*. Compare/contrast with [mai-dxo](mai-dxo.md), which uses multi-agent orchestration on harder NEJM-CPC cases.
