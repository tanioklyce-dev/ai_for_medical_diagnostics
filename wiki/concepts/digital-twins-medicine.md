---
type: concept
title: Digital twins in medicine
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [task/prognosis, task/treatment-planning, deployment, evaluation/prospective-trial]
---

# Digital twins in medicine

A **medical digital twin** is a dynamic, data-linked computational representation of an individual patient that updates over time and supports forecasting, simulation, and treatment optimization. Research interest exploded in 2025, but the field is fragmented and definitionally murky.

## NASEM definition

Per the National Academies of Sciences, Engineering, and Medicine, a true medical digital twin requires three elements:

1. **Personalization** — patient-specific.
2. **Dynamic updating** — responsive to new data over time.
3. **Predictive capability** — forecasts future state or response.

A 2025 scoping review (Sadée et al.) in *npj Digital Medicine* assessed **149 human digital twin studies published 2017–2024** and found:

- **Only 12.1% (18 of 149)** satisfied the full NASEM definition.
- **Only 19%** of systems were tested in real healthcare environments.
- Most labelled "digital twin" work is closer to traditional patient simulation or single-snapshot risk prediction.

## The volume explosion

| Year | Publications | Patent filings (G16H class) |
|---|---|---|
| 2015 | 0 | 0 |
| 2017 | 0 | 106 |
| 2018 | 1 | 292 |
| 2020 | 16 | 667 |
| 2022 | 55 | 2,395 |
| 2024 | 176 | 4,926 |
| 2025 | **372** | 4,087* |

*The 2025 patent dip reflects publication lag, not a real decline.

The publication and patent curves match a hype-cycle rise, but rigorous studies are a small fraction.

## Where the rigorous evidence lives (2025 trials)

| Trial / Platform | Domain | Design / Result |
|---|---|---|
| **Twin Health "Whole Body Digital Twin"** | Type 2 diabetes | RCT (n=150). **71% achieved HbA1c <6.5%** within 12 months **while safely reducing blood sugar–lowering medication intake**. |
| Mayo Clinic phase II | Breast cancer | Extended adaptive-therapy approach to breast cancer using digital twin elements. |
| **ACTOv** phase II RCT (n=80) | Ovarian cancer | Adaptive therapy with digital twin–guided dosing. |
| Prostate cancer pilot | Prostate cancer | Adaptive therapy using digital twins concluded 2025; significantly increased survival (Zhang et al., 2022 baseline). |

The Twin Health diabetes RCT is the strongest result: it's an RCT with a clinically meaningful primary endpoint (HbA1c control with medication reduction) — exactly the kind of evidence the [arise-network](../entities/arise-network.md) *State of Clinical AI Report* says is missing for most clinical AI.

## Where digital twins fit in diagnostics specifically

This is mostly a **treatment-optimization** tool category, not a diagnostic one. But there are diagnostic-adjacent uses:
- Diagnostic *prognosis* — twin-based forecasting of disease progression after diagnosis.
- **Companion diagnostics** for adaptive therapy — twin guides dosing based on individual response.
- *Risk stratification* for screening — modeling individual-specific risk to inform diagnostic test ordering.

## Open questions

- **Definition convergence** — the NASEM criteria are restrictive; most "digital twin" work fails them. Will the field tighten its terminology, or will the term keep diluting?
- **Data infrastructure** — true dynamic updating requires continuous data streams (wearables, EHRs, labs). Few institutions have this in production.
- **Regulatory framework** — adaptive twin-driven dosing changes what's "the device." How does FDA's [fda-510k-pathway](fda-510k-pathway.md) / PCCP framework adapt?
- **Equity** — twin models trained on well-monitored patients may underperform for under-monitored populations (raised in Ch. 6.4 ethics framing).

## Related
- [clinical-validation](clinical-validation.md) — twins are an extreme test case of the validation gap.
- [medical-imaging-ai](medical-imaging-ai.md) — many twins ingest imaging features.
- [ai-index-2026](../sources/ai-index-2026.md) — primary source.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2 Digital Twins highlight box, p. 278–279)
