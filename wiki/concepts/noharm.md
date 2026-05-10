---
type: concept
title: NOHARM — clinical safety benchmark for LLMs
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [evaluation/external-validation, concern/safety, task/management]
---

# NOHARM

A specialist-validated benchmark that quantifies **how often LLM medical recommendations could harm patients**. Built and maintained by the [ARISE Network](../entities/arise-network.md). *Wu, Goh et al., ArXiv Dec 2025.*

## Construction

- **100 authentic primary-care–to–specialist consult cases** across 10 specialties.
- **4,249 possible management actions** per case, with **12,747 expert annotations** distinguishing recommended / acceptable / inappropriate / severely harmful.
- Severity is the central axis: NOHARM specifically measures *severe harm* outcomes, not just accuracy.

## Headline 2025 results

Across **31 LLMs** including commercial RAG-based clinical systems:

- **Severe harm rate: up to 22% of cases.**
- **Errors of omission account for 77% of severe harms** — i.e., the LLM fails to recommend a critical test or treatment that the case actually requires. Commission errors (suggesting something harmful) are the smaller share.
- General AI/medical "knowledge" benchmarks (MedQA etc.) correlate only moderately with NOHARM (R = 0.61–0.64) — **knowledge benchmarks do not reliably predict clinical safety.**
- The best LLMs outperform generalist physicians on NOHARM by ~10%.
- Three-agent **"advisor + guardian" LLM systems** show ~6× higher odds of top-quartile safety vs solo models — multi-agent architectures have a measurable safety advantage.
- Commercial clinical RAG products (#1 and #3 ranks at time of report) score well, suggesting the gap between research LLMs and deployed clinical systems is meaningful.

## Why it matters

This is **the first benchmark** to put hard numbers on the gap between LLM accuracy and LLM safety in real consult contexts. Until NOHARM, the dominant safety frame was MedQA-style accuracy or NEJM CPC differentials, neither of which speaks to omission-of-critical-action — the failure mode that actually hurts patients.

NOHARM is referenced throughout [ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) and underpins the cautionary framing in the [Benchmarks & Evaluations](../sources/arise-state-of-clinical-ai-2026.md) section. It is also the foundational component of ARISE's broader **MAST (Medical AI Superintelligence Test)** vision, a leaderboard at `bench.arise-ai.org`.

## Position vs. other safety benchmarks

- **MetaMedQA** (Griot Yuskel Nature Communications Jan 2025): tests whether LLMs *recognize* unanswerable / malformed questions. Found 0% recall at recognizing unanswerability. Different axis (metacognition), same direction.
- **CRAFT-MD** (Johri Rajpurkar Nature Medicine Jan 2025): static-vignette → multi-turn dialogue accuracy collapse (GPT-4 0.82 → 0.63). Tests *robustness*, not safety per se.
- **HealthBench** ([healthbench](healthbench.md)): rubric-graded conversational quality. Closer to capability evaluation than safety.
- NOHARM is uniquely focused on **severe-harm probability in realistic consult cases**, which is the clinically actionable safety question.

## Caveats

- Specialist consult cases — generalization to ED triage, ambient-care, or chronic-disease management is not directly tested.
- The "best LLMs outperform generalist physicians by 10%" claim is benchmark-specific; it does *not* mean LLMs are safer than physicians in deployment.
- Commercial RAG products being top-ranked deserves independent replication.

## Cross-references

See the broader hallucination/factuality story at [ai-hallucination-medical](ai-hallucination-medical.md), and the multi-agent architectural angle at [agentic-clinical-ai](agentic-clinical-ai.md).
