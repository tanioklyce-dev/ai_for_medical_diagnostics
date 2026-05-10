---
type: concept
title: Medical imaging AI
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md, ../sources/ogut-ai-clinical-medicine-2025.md]
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

## 2025 prospective imaging RCTs (primary citations from ARISE 2026)

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) gives us per-paper detail on the 2025 prospective imaging cohort:

- **Vara MG mammography** (Eisemann, Katalinic et al. *Nature Medicine* Jan 2025) — Germany, 12 sites, 463,094 women (260,739 with AI). BCDR **6.7 vs 5.7 per 1,000** (17.6% increase, CI 5.7–30.8%); recall rate slightly *lower* (37.4 vs 38.3 per 1,000). 204 cancers caught via "safety-net" alerts (many DCIS). Stronger PPV for both recall and biopsy. The cleanest "AI improves screening without false-alarm tax" data point in 2025.
- **Brainomix 360 stroke** (Nagaratnam, Harston et al. *The Lancet* Dec 2025) — England NHS, 26 hospitals, longitudinal evaluation. EVT (endovascular thrombectomy) increased **2.3% → 4.6%** at AI sites vs **1.6% → 2.6%** at non-AI hospitals (62.5% relative). Door-in-door-out **192 → 128 minutes**. Higher odds of good functional outcomes (OR 1.16). The largest real-world stroke-AI evaluation to date.
- **EyeFM RCT** (Wu, Dai et al. *Nature Medicine* Aug 2025) — 16 ophthalmologists, 668 patients, China. Diagnostic rate **75% → 92%** with AI; referral rate **81% → 92%**. Higher follow-up compliance (70% vs 49%) and referral action rates (38% vs 20%) in the AI group.
- **Cardiac amyloidosis from 4-chamber echo** (Slivnick, Pellikka et al. *European Heart Journal* Jul 2025) — multicenter (n=2,719). AUROC **0.93** vs traditional clinical scores (transthyretin CA score 0.74, increased wall thickness 0.80).
- **Spirometry interpretation** (Doe, Man et al. *NEJM AI* Jul 2025) — 133 PCPs / NPs randomized to AI assistance (CNN, ArtiQ.Spiro). **Top-diagnosis accuracy +9 points**, COPD identification +16 points. AI also improved technical-quality grading.
- **AI-ECG cirrhosis screening** (Simonetto, Shah et al. *Nature Medicine* Dec 2025) — 98 primary care teams, 15,596 patients, cluster RCT. New advanced CLD diagnoses **0.5% → 1.0%** (OR 2.1); among ECG-ML-positive patients, diagnoses rose 4% vs 1% (OR 4.4).
- **Smart Match transfusion ML** (Bishara, Eng et al. *NEJM AI* Nov 2025) — 24,003 silent prospective surgeries, AUROC 0.94, outperformed clinicians and MSBOS guidelines.

These prospective deployments — paired with the LCTfound, MUSK, EchoPrime, EchoNext, PRESENT-SHD foundation models and the [echonext](../entities/echonext.md), [present-shd](../entities/present-shd.md) ECG screening pair — represent the **strong-evidence track** for medical imaging AI.

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

See [fda-510k-pathway](fda-510k-pathway.md) for the regulatory landscape underpinning this market.

## Related
- [clinical-validation](clinical-validation.md) — most published evaluations are not on real patient data.
- [fda-510k-pathway](fda-510k-pathway.md) — the regulatory route for nearly all cleared imaging AI.
- [ambient-ai-scribes](ambient-ai-scribes.md), [llm-clinical-reasoning](llm-clinical-reasoning.md), [agentic-clinical-ai](agentic-clinical-ai.md) — adjacent clinical AI categories that are *not* imaging.

## Earlier landmark imaging-AI primary citations

The [Ogut 2025 review](../sources/ogut-ai-clinical-medicine-2025.md) surfaces a useful pre-2025 citation chain for the imaging-AI primary literature:

- **Rodriguez-Ruiz et al. *J. Natl. Cancer Inst.* 2019** — stand-alone AI mammography on par with the average of **101 radiologists** at distinguishing malignant from benign lesions. Predates Vara MG; the original "AI matches radiologist average" mammography result.
- **Mayo et al. *J. Digit. Imaging* 2019** — AI-augmented mammography CAD reduced false-positive marks by **69%** vs traditional CAD. Pre-Vara-MG primary for the false-alarm-reduction story.
- **Gulshan et al. *JAMA* 2016** — deep learning for diabetic retinopathy detection in retinal fundus photographs (sensitivity comparable to ophthalmologists). The foundational ophthalmology AI paper.
- **Försch, Klauschen, Hufnagl, Roth *Dtsch. Arztebl. Int.* 2021** — **pathologist sensitivity for lymph node metastasis detection rose 83% → 91% when paired with AI** as second reader. Pathology-specific evidence for the human-AI synergy pattern.
- **Attia et al. *Lancet* 2019** — AI identifies asymptomatic atrial fibrillation **from normal-sinus-rhythm ECG**. The original opportunistic-ECG-screening paper; [echonext](../entities/echonext.md) and [present-shd](../entities/present-shd.md) descend from this lineage.

These are useful for tracing the genealogy of the 2025 prospective imaging-RCT cohort — most current results are direct successors of these 2016–2021 landmark studies.

## Caveat: the illusion of multimodal readiness

**Gu, Vozila et al., ArXiv Oct 2025** — leading multimodal medical models score well on benchmark questions even when key visual inputs are *missing or perturbed*. Models gave the correct answer well above chance on incomplete questions, with high-confidence chain-of-thought explanations describing visual features that were not present. Strong multimodal benchmark scores often reflect **shortcut learning** rather than visual grounding. ARISE flags this as a critical caveat: benchmark success ≠ clinical readiness.

## Sources
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (Foundational Methods + Applied AI sections — primary citation chain for 2025 prospective trials)
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2, p. 269–271, 273–276)
- [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md) (citation map for 2016–2021 landmark imaging-AI papers)
