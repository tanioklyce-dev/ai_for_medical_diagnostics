---
type: entity
title: Delphi-2M — generative transformer for human disease trajectories
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/arise-state-of-clinical-ai-2026.md]
tags: [model-family/foundation-model, task/prognosis, task/screening, evaluation/auc, evaluation/external-validation]
---

# Delphi-2M

A GPT-2-based generative transformer trained on >400,000 UK Biobank participants and externally validated on 1.9M Danish individuals. Predicts the *next* disease and its timing across **>1,000 conditions**, and can sample entire lifetime disease trajectories up to 20 years ahead. *Shmatko, Gertsung et al., Nature Sept 2025.*

## What's novel

Delphi-2M represents each patient as a sequence of **(token, age) pairs** drawn primarily from ICD-10 disease tokens. Treating longitudinal medical records as a tokenized stream makes generative-LLM techniques directly applicable to disease forecasting. This is one of the two flagship 2025 examples of the **medical-event tokenization** paradigm (the other being Epic's [comet](comet.md), which goes much larger).

## Performance

- AUC 0.76 for next-disease diagnosis on internal data, 0.67 external. AUC 0.70 at the 10-year horizon.
- Exceeds or matches conventional task-specific clinical risk scores for cardiovascular disease, dementia, and death.
- *Underperforms HbA1c* for diabetes specifically — a useful reminder that scale ≠ specialty.
- Disease clusters that emerge from the model's learned embeddings mirror known medical groupings, suggesting potential utility for genomic-association studies.

## Why ARISE highlights it

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) treats Delphi-2M as evidence that **prediction-side foundation models** can produce realistic, interpretable lifetime trajectories from routine EHR data. This sits alongside the [evo-2](evo-2.md) genomic FM and [alphafold-3](alphafold-3.md) co-folding work as part of the upstream foundation-model layer feeding into clinical AI — but unlike those, Delphi-2M is *directly* in the patient-prediction loop.

## Limitations

- ICD-coded EHR data only; misses structured labs, medications, free-text notes.
- External validation gap (0.76 internal → 0.67 external) is consistent with the [medical-imaging-ai](../concepts/medical-imaging-ai.md) generalization story — robust but degraded under distribution shift.
- No prospective trial yet; "earlier preventive interventions" is the stated aspiration, not a demonstrated outcome.
