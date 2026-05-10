---
type: concept
title: Medical imaging AI
added: 2026-05-10
updated: 2026-05-10
sources: [[[ai-index-2026]]]
tags: [modality/radiology, modality/pathology, modality/cardiology, modality/ophthalmology, task/detection, task/classification, task/segmentation, evaluation/external-validation]
---

# Medical imaging AI

The dominant area of clinical AI deployment by every measure: 76.6% of FDA-cleared AI/ML devices are radiology, prospective imaging trials grew 28.5% YoY in 2025, and most clinical foundation-model development is happening here. But the field also has structural disadvantages relative to general-domain AI: data scarcity, fragmentation, and weak cross-model benchmarking.

## The data scarcity problem

Medical imaging training data is roughly **100x smaller** than general-domain in raw sample count.

| Model | Training data |
|---|---|
| MAIRA-2 (radiology-focused) | ~1.4M chest radiographs |
| DINOv3 (general-purpose ViT) | 1.7B unlabeled natural images |
| RadFM (multimodal medical) | ~16M mixed 2D/3D scans + clinical text |
| OpenCLIP (LAION-5B) | ~5.85B image–text pairs |

Data scarcity is especially pronounced for **3D modalities (CT, MRI)**. Fragmentation across institutions further limits scale. Newer biomedical VLM datasets are widening: MEDICAT (2020) → BIOMEDICA 24M (2025), with breadth across specialties and modalities.

## Notable models by clinical discipline (2025–26)

| Discipline | Notable research releases | Analogous FDA-cleared products |
|---|---|---|
| **Cardiology** | EchoJEPA (2026), PanEcho (2025), EchoFM, EchoPrime | Bunkerhill ECG-EF, Heartflow Plaque Analysis |
| **Oncology** | MUSK (2025) | Allix5 (Clairity, 2025), Transpara 2.1.0 (2024) |
| **Ophthalmology** | EyeCLIP, Meta-EyeFM, RETFound-Green | CLARUS (700) Carl Zeiss (2025) |
| **Pathology** | Virchow2G (2026), KRONOS, VORTEX, Threads, mSTAR, PRISM2, MPath, H-Optimus-0 | ArteraAI Prostate, Ibex Prostate Detect (both 2025) |
| **Radiology** | MedGemma 1.5 (2026), COLIPRI (2026), TTE 3D CT, 3DINO-ViT, CT-FM, RadFM, **Merlin** | BriefCase Triage CARE Multi-triage CT Body, a2z Unified Triage, Bunkerhill BMD/AAQ, Brainomix 360 Triage Stroke, Ezra Flash (all 2025–26) |

> **Merlin** (radiology) is notable for demonstrating that a highly capable CT foundation model could be trained on a **single 40GB GPU** by leveraging both radiology reports and ICD codes — a pointer to making medical foundation models accessible in resource-constrained settings.

## The cross-model benchmarking gap

Medical imaging AI **lacks the standardized cross-model benchmarks** that general ML enjoys (e.g., ImageNet, GLUE). Models in different specialties are typically evaluated on different datasets, making direct cross-discipline comparison nearly impossible.

Early efforts to fix this in 2025:
- **MICCAI 2025 challenges**
- **CHIMERA**
- **UNICORN**

**Human-centered evaluation** (clinicians manually reviewing model outputs) is becoming more common in publications and provides stronger evidence of clinical utility than purely lexical metrics.

## Prospective clinical trials are growing

| Year | Imaging AI prospective trial papers |
|---|---|
| 2017 | 14 |
| 2020 | 99 |
| 2022 | 203 |
| 2024 | 417 |
| **2025** | **536** (+28.5%) |

Recent high-profile examples:
- **MASAI** — RCT of AI-assisted mammography screening accuracy.
- **NOTIFY-1, NOTIFY-EXTEND** — tested whether early heart-disease signals AI flagged on routine CT scans changed clinician prescribing of preventive cholesterol medication.

## Industry concentration

Clearance rankings (cumulative 2016–25):
- GE Healthcare 93, Siemens Healthineers 82, Shanghai United Imaging 38, Philips 36, Canon 35, Aidoc 30, Samsung 20, iSchemaView 20, Hyperfine 12, Viz.ai 12, Clarius Mobile Health 11, Brainlab 10, Zebra Medical Vision 9, RaySearch 8, Qure.ai 8.

See [[fda-510k-pathway]] for the regulatory landscape underpinning this market.

## Related
- [[clinical-validation]] — most published evaluations are not on real patient data.
- [[fda-510k-pathway]] — the regulatory route for nearly all cleared imaging AI.
- [[ambient-ai-scribes]], [[llm-clinical-reasoning]], [[agentic-clinical-ai]] — adjacent clinical AI categories that are *not* imaging.

## Sources
- [[ai-index-2026]] (Ch. 6.2, p. 269–271, 273–276)
