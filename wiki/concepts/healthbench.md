---
type: concept
title: HealthBench — physician-grounded conversational benchmark (OpenAI)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [evaluation/external-validation, task/diagnosis, task/management]
---

# HealthBench

OpenAI's 2025 benchmark for evaluating LLM performance on **realistic, multi-turn health conversations** — built specifically to address three gaps the company identified in prior medical-LLM evaluation: (1) lack of real-world / open-ended impact, (2) lack of physician validation, (3) saturation of multiple-choice benchmarks. *Arora, Singhal et al., ArXiv May 2025.*

## Construction

- **5,000 health conversations**, average 2.6 turns.
- **262 physicians from 60 countries** generated **48,562 rubric criteria** — each conversation has a custom physician-validated rubric for grading model responses.
- Five behavioral axes: communication quality, response depth, etc.; seven clinical themes including emergency referrals.
- "HealthBench Consensus" subset reflects high inter-physician agreement; "HealthBench Hard" leaves room for further model improvement.

## Performance trend

Steady, significant progress across the GPT family:

- GPT-3.5 → 16%
- GPT-4o → 32%
- o3 → 60%

Reasoning models particularly excel at communication quality and emergency-referral identification. Lower performance in *context-seeking* and *health-data tasks*. A "worst of n" evaluation surfaces reliability — newer models perform best across multiple samples.

## Why ARISE included it

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) treats HealthBench as one of three benchmarks redefining what "good clinical AI evaluation" looks like in 2025 — alongside [medhelm](medhelm.md) (Stanford, EHR-grounded) and [medagentbench](medagentbench.md) (FHIR-EHR action evaluation). Together, this trio represents the field's response to the *over-saturation of multiple-choice / vignette benchmarks* documented in Bedi/Shah JAMA Jan 2025 (see [clinical-validation](clinical-validation.md)).

## Caveats

- **Synthetically generated conversations**, not real patient interactions. Better than static MCQ but not yet real-clinical-data.
- OpenAI-built benchmark evaluating OpenAI models — independent reproducibility is essential before treating leaderboard rankings as field-wide ground truth.
- Physician rubrics are validated against multi-country consensus, but cultural / health-system variation is implicit.

## Position vs. NOHARM

[noharm](noharm.md) measures *severe-harm probability* on consult cases. HealthBench measures *response quality* on patient conversations. Different layers of the safety/capability stack — both should be tracked.
