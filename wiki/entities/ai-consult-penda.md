---
type: entity
title: AI Consult — Penda Health × OpenAI deployment (Kenya)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [task/diagnosis, evaluation/prospective-trial, evaluation/external-validation, modality/primary-care, deployment]
---

# AI Consult (Penda Health, Kenya)

The first **prospective evaluation of a frontier-LLM clinical copilot in real-world care delivery** (per [ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md)). Penda Health, a Kenyan primary/urgent care provider, partnered with OpenAI to deploy a GPT-4o-based "safety net" copilot at 15 clinics. Between Jan and Apr 2025, **39,849 visits** were logged: 20,589 with AI Consult active and 18,990 without.

## How it works

After multiple rounds of prompt engineering, AI Consult ran silently in the background of the encounter and surfaced one of three traffic-light flags — green / yellow / red — across four encounter dimensions: **documentation, investigations, diagnosis, treatment**. The clinician was not required to act on the flag, but flag rates were measured before and after Penda's "active deployment" push to encourage usage.

## Headline outcomes

- **16% relative reduction in diagnostic errors.**
- **13% relative reduction in treatment errors.**
- 32% reduction in history-taking errors, 10% in investigations.
- Number-needed-to-treat: 18.1 visits per diagnostic-error averted, 13.9 per treatment-error averted. Extrapolated to Penda's ~400,000 annual visits → ≈22,102 fewer diagnostic errors and ≈28,880 fewer treatment errors per year.
- Rate of "left in red" (i.e., visits ending with a critical AI flag still unaddressed) fell from 45% to 35% over the trial — clinicians appeared to *learn* to avoid common errors up front.
- Patient-reported outcomes were equivocal between groups.
*Korom, Singhal et al., ArXiv Jul 2025.*

## Why this matters

Almost every other "AI vs physicians" headline in 2025 came from simulated cases or retrospective benchmarks. AI Consult is **prospective, real care, large n, and outside the U.S.** — addressing three of the [clinical-validation](../concepts/clinical-validation.md) gaps simultaneously. ARISE flags it as the marquee example of the strong-evidence track for LLM-based AI specifically (vs. narrow imaging tools like Brainomix 360 or Vara MG, which are deep-learning, not LLM).

## Caveats

- Single-vendor (OpenAI), single-health-system (Penda), single-country deployment — generalization to OECD primary care is untested.
- "Errors" are adjudicated by a physician rater panel against a Likert rubric, not against patient outcomes.
- Documentation, investigation, and prompt-engineering iteration time before the trial began is non-trivial, complicating off-the-shelf replicability claims.
