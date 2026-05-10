---
type: source
title: Automated Keratoconus Screening with Corneal Topography Analysis (Maeda, Klyce, Smolek, Thompson 1994)
authors: [Naoyuki Maeda, Stephen D. Klyce, Michael K. Smolek, Hilary W. Thompson]
published: 1994-05
ingested: 2026-05-10
source_path: raw/2749.pdf
journal: Investigative Ophthalmology & Visual Science (IOVS)
volume: 35(6), 2749–2757
pages: 9
license: not specified (copyright Association for Research in Vision and Ophthalmology, 1994)
tags: [modality/ophthalmology, task/screening, task/classification, evaluation/external-validation, model-family/expert-system, historical]
---

# Automated Keratoconus Screening With Corneal Topography Analysis (Maeda, Klyce, Smolek, Thompson 1994)

> The first **explicitly AI-labeled** ophthalmology screening system the [stephen-klyce](../entities/stephen-klyce.md) group published. A 200-cornea study using **discriminant analysis + a rule-based expert system** to classify keratoconus from videokeratoscope data. Senior author Klyce; first author Naoyuki Maeda (postdoctoral); engineering / statistics co-authors Smolek and Thompson. *Investigative Ophthalmology & Visual Science* 35(6):2749–2757, May 1994. Supported by PHS grants EY03311 and EY02377 (continuous funding from the 1984 paper) and the Louisiana Lions Eye Foundation.

## Summary

Building on the quantitative-topography platform established in [klyce-computer-assisted-corneal-topography-1984](klyce-computer-assisted-corneal-topography-1984.md), this paper realizes the **`diagnose` module** that the 1984 paper sketched but deferred. Eight quantitative indices derived from TMS-1 videokeratoscope data (Computed Anatomy, NY) — five of them new in this work (DSI, OSI, CSI, IAI, AA) plus three preexisting (SimK1, SimK2, SAI) — are run through linear discriminant analysis (SAS 6.06) producing a composite **Keratoconus Prediction Index (KPI)**. KPI is then embedded inside a **Pascal-implemented rule-based expert system** whose binary decision tree distinguishes four output categories: non-keratoconus, borderline, central-steepening keratoconus, peripheral-steepening keratoconus.

The training set contains 100 corneas across 8 categories (keratoconus, normal, keratoplasty, epikeratophakia, photorefractive keratectomy, radial keratotomy, contact-lens-induced warpage, other); the validation set contains another 100. With the optimum KPI cutoff at 0.23, the expert system achieves **89% sensitivity, 99% specificity, 96% accuracy** on the validation set, a **statistically significant improvement** over discriminant analysis alone (68% sensitivity; McNemar *p* = 0.016). All false positives in the validation set are post-keratoplasty eyes with localized abnormal steepening; all false negatives have keratoconus in the contralateral eye (clinically consistent with subclinical or asymmetric presentations).

The paper explicitly labels the system as artificial intelligence: *"An expert system is an artificial intelligence approach that contains a modifiable knowledge base (rules and facts), an interface to users, and an interface engine that makes logic-based decisions."* It cites the contemporary medical-expert-system literature (Marchevsky 1991 on lung cancer cytology; Rubin 1992 on dermatopathology) as the methodological context. This places the work alongside Pathfinder (Heckerman, Horvitz, Nathwani 1992; see [eric-horvitz](../entities/eric-horvitz.md)) and MYCIN (Buchanan & Shortliffe 1976; cited in [ogut-ai-clinical-medicine-2025](ogut-ai-clinical-medicine-2025.md)) as part of the early-1990s expert-system wave in medical AI — but specifically for ophthalmology.

## Key claims and findings

### Eight indices for topographic characterization (Figures 1, 3)

| Index | Sensitivity to |
|---|---|
| **SimK1, SimK2** (Simulated Keratometry, preexisting) | central corneal steepening; cylindrical power |
| **SAI** (Surface Asymmetry Index, preexisting) | topographic asymmetry of decentered cones |
| **DSI** (Differential Sector Index, **new**) | localized abnormal steepening in the periphery |
| **OSI** (Opposite Sector Index, **new**) | greatest power difference between opposing sectors |
| **CSI** (Center/Surround Index, **new**) | centrally-located steepening |
| **IAI** (Irregular Astigmatism Index, **new**) | short-range power irregularity along meridians |
| **AA** (Analyzed Area, **new**) | ratio of interpolated to total mire-encircled corneal area |

DSI, OSI, and CSI are computed by dividing the corneal surface into 8 pie-shaped sectors (45° each), rotating the pattern in 1.41° steps to find max contrast. IAI averages inter-ring power variation along every semimeridian. AA characterizes data completeness.

### Discriminant analysis → KPI

Using all 8 indices on the 100-cornea training set:

> KPI = 0.30 + 0.01 × (−41.23 − 0.15·DSI + 1.18·OSI + 1.49·CSI + 4.13·SAI − 0.56·SimK1 + 1.08·SimK2 − 3.74·IAI + 0.10·AA)

Cases with KPI > 0.30 (optimum cutoff for discriminant analysis alone) are classified keratoconus. Training: 86% sens, 100% spec, 97% acc. **Validation: 68% sens, 99% spec, 90% acc.** Low sensitivity → insufficient for clinical screening alone (Discussion, p. 2756).

### Expert-system decision tree (Figure 5)

A Pascal binary decision tree using KPI + SimK2 + DSI + OSI + CSI in nested rules:

- KPI < 0.23 *or* SimK2 < 38.5 → non-keratoconus
- 0.23 ≤ KPI < 0.30 → borderline → further DSI/OSI/CSI thresholds distinguish central vs peripheral keratoconus
- KPI ≥ 0.30 → keratoconus → further DSI/OSI thresholds distinguish central vs peripheral

Optimum KPI cutoff lowered from 0.30 (discriminant alone) to **0.23** (expert system) — i.e., the rule layer absorbs additional sensitivity safely because the secondary indices catch the false positives that would otherwise creep in at the lower threshold.

### Validation results (Tables 4, 5, 6)

| Method | Sensitivity | Specificity | Accuracy |
|---|---|---|---|
| Discriminant analysis (KPI ≥ 0.30) — training | 86% | 100% | 97% |
| Discriminant analysis (KPI ≥ 0.30) — validation | 68% | 99% | 90% |
| **Expert system (KPI cutoff 0.23) — training** | **100%** | **96%** | **97%** |
| **Expert system (KPI cutoff 0.23) — validation** | **89%** | **99%** | **96%** |

McNemar's test (with small-frequency correction) gives *p* = 0.016 for the sensitivity improvement (89% vs 68%) on the validation set.

### Failure-mode analysis (Discussion, p. 2756)

- All 4 false-positives are **post-keratoplasty** eyes — localized abnormal steepening on the corneal graft fools the rule system in the absence of clinical context.
- 3 false-negative cases all have **clinically diagnosed keratoconus in the contralateral eye**; two of the maps resemble contact-lens-induced warpage, one resembles pellucid marginal degeneration.
- The authors recommend the system as a screening tool that flags maps for clinician review, not as an autonomous diagnostic system — explicitly anticipating the human-in-loop framing that recurs through current ARISE 2026 era arguments (see [clinical-validation](../concepts/clinical-validation.md)).

## Why this paper matters

For this wiki:

1. **First AI-labeled ophthalmology screening system in the [stephen-klyce](../entities/stephen-klyce.md) lineage.** Rung two of the imaging-AI ladder for corneal topography (rung one: [klyce-computer-assisted-corneal-topography-1984](klyce-computer-assisted-corneal-topography-1984.md); rung three: Maeda/Klyce/Smolek 1995 neural network, PubMed 7775110, not yet ingested).
2. **Same expert-system era as [eric-horvitz](../entities/eric-horvitz.md)'s Pathfinder** (1992). Two parallel medical-AI research programs — different specialties, similar methodology (rule-based decision support over hand-engineered features), both directly anticipating modern AI-augmented diagnostic systems.
3. **Indices still used today.** KPI, DSI, OSI, CSI, IAI, AA, and SAI remain standard inputs to modern keratoconus-screening algorithms, including deep-learning systems (see Lozano-Castaneda et al. *Diagnostics* MDPI 2023 systematic narrative review). The 1994 feature-engineering work has outlasted its 1994 classifier.
4. **Realizes the 1984 vision.** Klyce's 1984 paper sketched a `diagnose` module that would identify shape anomalies; this paper builds exactly that, ten years later, on a TMS-1 videokeratoscope that obviates the manual-digitization bottleneck.

## Notes

- **Author context.** Naoyuki Maeda was a postdoctoral fellow / visiting scientist; Stephen D. Klyce was the senior PI. Michael K. Smolek was a research engineer and would go on to author the 1997 neural-network systematic-comparison paper with Klyce. Hilary W. Thompson contributed statistical methodology (discriminant analysis).
- **TMS-1 device context.** Computed Anatomy (NY) developed the TMS-1 videokeratoscope, which automated the manual-digitization bottleneck that constrained the 1984 system. The 1994 work is thus the first to use *integrated* automated topography + classification, a system Klyce has consulted on the commercial-vendor side of (NIDEK eventually acquired/extended this lineage).
- **Citation precedence**: this is the primary source for the **KPI** index and the **DSI / OSI / CSI / IAI / AA** topographic indices used across the modern keratoconus literature.
- **Adjacent sources to ingest next**: Maeda/Klyce/Smolek *Neural network classification of corneal topography: preliminary demonstration* IOVS 1995 (PubMed 7775110); Smolek & Klyce *Current keratoconus detection methods compared with a neural network approach* IOVS 1997 (PubMed 9344352). Together these close the lineage from rule-based expert system → multilayer perceptron in the same research group.

## Entities and concepts touched

- [stephen-klyce](../entities/stephen-klyce.md) — senior author; primary AI-labeled implementation in his publication record.
- [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) — rung two of the lineage this concept page traces.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — ophthalmology imaging-AI section.
- [agentic-clinical-ai](../concepts/agentic-clinical-ai.md) — expert-system era ancestor of modern multi-agent / rule-based architectures (NOHARM advisor-guardian patterns resemble the KPI + rule-tree composition).
- [clinical-validation](../concepts/clinical-validation.md) — the 1994 authors explicitly position the system as screening + clinician confirmation, not autonomous diagnosis. Early articulation of the human-in-loop framing.
- [eric-horvitz](../entities/eric-horvitz.md) — parallel expert-system contemporary (Pathfinder 1992, same era, different specialty).
