---
type: entity
title: PRESENT-SHD — opportunistic SHD detection from ECG images and phone photos
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [modality/cardiology, task/screening, task/detection, evaluation/auc, evaluation/external-validation]
---

# PRESENT-SHD

An ensemble deep-learning model trained on **261,228 ECG image files** mapped to echocardiograms, capturing left ventricular hypertrophy, LV systolic dysfunction, severe valvular disease, septal abnormalities, and other structural heart disease (SHD) phenotypes. *Dhingra, Khera et al., JACC Mar 2025.*

## Why it's distinct from EchoNext

[echonext](echonext.md) operates on **structured ECG waveform data**. PRESENT-SHD operates on **ECG images** — including EHR screenshots and even **cell-phone photos of paper ECGs**. This makes it deployable in settings where structured 12-lead waveform data is unavailable: low-resource clinics, paper-only practices, telehealth photo-uploads.

## Performance

- AUROC 0.85–0.90 across six external cohorts for composite SHD detection.
- Stable across age, sex, and racial subgroups.
- Higher PRESENT-SHD probabilities predicted *incident* SHD or heart failure (forward-prognostic, not just current detection).
- Maintained accuracy on cell-phone photographs of ECG printouts and EHR screenshots — a key real-world robustness claim.

## Position in the field

Combined with [echonext](echonext.md), PRESENT-SHD represents the **opportunistic ECG-screening paradigm**: any ECG ever taken can be re-analyzed for cardiomyopathy/valve disease detection without a new test. ARISE flags this as a leading 2025 example of "repurposing abundant low-cost noninvasive data" — the dominant pattern across the [Applied AI & Demos](../sources/arise-state-of-clinical-ai-2026.md#applied-ai--demos-slides-93125) section.

## Limitations

- No prospective deployment evidence yet for either incident-disease detection or downstream care change.
- Image-quality variation in real-world phone photos is harder to characterize than in trial settings.
- "Stable across subgroups" is reported in published metrics; broader bias audit (per [clinical-validation](../concepts/clinical-validation.md)) is open.
