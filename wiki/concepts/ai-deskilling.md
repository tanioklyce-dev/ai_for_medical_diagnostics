---
type: concept
title: AI deskilling in clinical practice
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [concern/deployment, concern/safety, evaluation/external-validation]
---

# AI deskilling

The hypothesis that **continuous reliance on AI assistance erodes clinicians' independent skill**, manifesting as worse performance when the AI is unavailable. Closely related to but distinct from [automation-bias-medical-ai](automation-bias-medical-ai.md): automation bias is over-reliance on AI *while it is in use*; deskilling is degradation of unaided performance *after* prolonged AI use.

## The first hard 2025 evidence

**Budzyn, Mori et al., Lancet Gastroenterology & Hepatology Oct 2025** — multicenter retrospective observational study of 1,443 standard (non-AI) colonoscopies across four centers, comparing performance **3 months before vs 3 months after** the same endoscopists were exposed to AI polyp detection during the *Artificial Intelligence in Colonoscopy for Cancer Prevention* trial.

- Adenoma detection rate (ADR) **fell 28.4% → 22.4%** for the same endoscopists when AI was removed.
- Adjusted for sex, age, center, and other factors, AI exposure was associated with worse independent detection (OR 0.69).

This is the cleanest published deskilling signal in clinical AI to date. It's particularly striking because polyp detection is a perceptual task with *immediate* feedback (the polyp is on the screen) — settings where one might expect human skill to be most preserved.

## Implications

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) cites this as evidence that the "AI removed in 5 years" thought experiment matters. If routine AI exposure permanently degrades independent skill, then:

- Clinicians' fallback capacity (when AI is offline, miscalibrated, or wrong on a specific case) is reduced.
- Trainees who learn medicine *with* AI may never develop the skills the AI is reasoning over.
- The *implementation question* shifts: it is no longer whether AI improves average performance, but whether it improves performance *net of skill atrophy* across the system.

## Open questions

- Is deskilling reversible? Does a refresher period without AI restore baseline skill?
- Does the effect generalize beyond perceptual imaging tasks (polyp detection) to clinical reasoning under uncertainty (e.g., would routine LLM use erode physicians' diagnostic reasoning when forced off-AI)?
- How does deskilling interact with the [ambient-ai-scribes](ambient-ai-scribes.md) story? If >90% of clinical-note text becomes AI-generated (per the ARISE 10-prediction list), do clinicians lose narrative-reasoning skill alongside polyp detection?
- What governance mechanisms are appropriate — periodic AI-off audits, training requirements, malpractice-standard implications?

## Related

[automation-bias-medical-ai](automation-bias-medical-ai.md) is the contemporaneous risk; deskilling is the longitudinal one.
