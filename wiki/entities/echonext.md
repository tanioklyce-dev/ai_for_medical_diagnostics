---
type: entity
title: EchoNext — ECG-based deep learning for structural heart disease
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [modality/cardiology, task/screening, task/detection, evaluation/auc, evaluation/external-validation]
---

# EchoNext

A multitask convolutional neural network that predicts **structural heart disease (SHD)** directly from 12-lead ECG waveforms, demographics, and tabular ECG features. Trained on **>1.2 million ECG–echocardiogram pairs**. *Poterucha, Elias et al., Nature Jul 2025.*

## Performance

- Internal AUROC 85%, external 78–80% across multiple cohorts.
- Validation cohort (patients without prior echo who later had one for follow-up): AUROC 83%.
- On 150 ECGs, **outperformed cardiologists at SHD detection** (77% vs 64% accuracy). Cardiologists' accuracy improved when consulting EchoNext (69% with assistance).

## Why it matters

SHD (e.g., LV hypertrophy, severe valvular disease, cardiomyopathy) is **frequently undiagnosed** because the standard test — echocardiography — is operator-intensive and not deployed at population screening scale. EchoNext is the leading evidence that ECGs (cheap, ubiquitous, already in every clinic) can serve as an **opportunistic SHD screen**. Combined with [present-shd](present-shd.md) (which extends to phone photos of ECGs) and ROMIAE (acute MI rule-out), this is a hub of the 2025 ECG-AI story in [ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md).

## Limitations

- External AUROC drops to ~80%, the standard generalization haircut.
- "Outperforms cardiologists" is on a 150-ECG standalone read; integrated workflow performance is open.
- No prospective deployment trial; the next milestone is a head-to-head against current cardiology referral practice with patient outcomes.
