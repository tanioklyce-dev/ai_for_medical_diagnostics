---
type: entity
title: CoMET — Cosmos Medical Event Transformer (Epic)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [model-family/foundation-model, task/prognosis, task/prediction, deployment]
---

# CoMET (Epic Cosmos Medical Event Transformer)

A generative medical-event foundation model trained on **118 million patients / 115 billion events** from Epic's Cosmos dataset. By number of medical events used for training, this is the **largest medical foundation model published to date** (per [ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md)). *Waxler, Shah et al., ArXiv Nov 2025.*

## What it does

Autoregressively predicts what happens next along a patient's timeline: not just disease progression, but readmissions, length of stay, treatment response, and future diagnoses. Tokenizes a wide range of EHR elements (diagnoses, encounters, labs, medications) and explicitly inserts **time-interval tokens** between events so the model learns calendar-time spacing.

## Performance

- Across **78 real-world tasks** (diagnosis prediction, length of stay, readmissions, disease progression), CoMET outperformed or matched task-specific models — without fine-tuning or few-shot examples.
- Performance scales predictably with model size and training data scale, mirroring the standard LLM scaling-law story.

## Significance

CoMET takes the medical-event tokenization idea (also pursued by [delphi-2m](delphi-2m.md)) and pushes it to **Epic-scale**. Where Delphi-2M is a research artifact (UK Biobank), CoMET is a model trained on the actual data spine of US healthcare delivery — Epic's customer health systems represent ~50% of US hospital records. The model is slated to become accessible to researchers from Cosmos-participating organizations in **February 2026**.

## Caveats

- Access is limited to Cosmos-participating orgs (initially); not openly distributable like Delphi-2M.
- Internal-validation focus; cross-system / international generalization not yet established.
- Generative simulations are powerful but easily over-trusted — see [ai-hallucination-medical](../concepts/ai-hallucination-medical.md) for the broader fragility story.
- No prospective trial of clinical-decision-making informed by CoMET predictions; the "operations planning / decision support" use cases are aspirational.

## Position vs. Delphi-2M

Same paradigm (medical-event tokens), much larger scale (118M patients vs 400k), and EHR-style training data (Cosmos vs UK Biobank cohort). CoMET predicts a wider event vocabulary (operations + diagnoses); Delphi-2M is more focused on disease-trajectory simulation. ARISE treats the pair as the **two flagship 2025 examples of medical-event foundation models**.
