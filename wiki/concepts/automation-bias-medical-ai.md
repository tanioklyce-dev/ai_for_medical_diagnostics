---
type: concept
title: Automation bias in medical AI
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [concern/deployment, concern/safety, evaluation/external-validation, task/diagnosis]
---

# Automation bias in medical AI

The well-known human-factors phenomenon — clinicians **over-defer to algorithmic outputs**, particularly when the algorithm has been shown to be helpful in general — applied to LLMs and clinical AI. Long studied for diagnostic-imaging CADx and rule-based alerts; in 2025, it became a measurable safety concern for **LLM-based clinical decision support**.

## The 2025 evidence

**Qazi, Alizai et al., medRxiv Sept 2025** — RCT of n=44 *AI-trained* physicians (those who had completed a 20-hour AI-literacy program), each reviewing up to 6 clinical vignettes (264 cases total). Half saw ChatGPT-4o suggestions; in 3 of the 6 vignettes those suggestions contained deliberate, detectable errors.

- Physicians exposed to flawed LLM recommendations achieved **73% accuracy** vs **85% for those receiving error-free advice** (pre-specified rubric).
- Top-choice diagnosis accuracy: 91% control vs 76% treatment, adjusted difference.
- Voluntary AI consultation rates were similar across groups (69% vs 67%) — physicians did not self-protect by avoiding AI more often when errors were planted.

This sits next to the same group's prior result (Qazi/Alizai medRxiv Jul 2025) that AI-trained physicians using *error-free* GPT-4o achieved a 27-percentage-point improvement vs conventional resources (43% → 71%). So **the same intervention helps when the AI is right and hurts when it isn't** — and clinicians can't reliably tell.

## Why this matters

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) flags this as one of three workflow-level safety concerns alongside [ai-deskilling](ai-deskilling.md) and the optimization paradox. The implication for deployment: **AI-literacy training is necessary but not sufficient**. Interface safeguards that *actively prevent* routine deference to LLM output are required. Candidate mechanisms (still understudied):

- Explicit uncertainty surfacing (related to the [ai-hallucination-medical](ai-hallucination-medical.md) failure family — models that don't know what they don't know cannot generate reliable uncertainty signals).
- Forcing-function workflows that require independent clinician reasoning *before* AI output is shown.
- Architectures that detect divergence between clinician's working hypothesis and AI suggestion, and route divergent cases for additional review.

## Open questions

- Does automation bias compound with [ai-deskilling](ai-deskilling.md) over months/years of routine AI use? The deskilling RCT only measured 3 months.
- Does the bias scale with stakes — does it matter more in high-acuity ED settings vs low-acuity primary care?
- Are AI-naive clinicians at higher risk than AI-trained ones, or is it the reverse (trained clinicians trust the AI more because they've internalized its general competence)?
