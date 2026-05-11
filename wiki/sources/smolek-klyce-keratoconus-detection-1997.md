---
type: source
title: Current Keratoconus Detection Methods Compared With a Neural Network Approach (Smolek & Klyce 1997)
authors: [Michael K. Smolek, Stephen D. Klyce]
published: 1997-10
ingested: 2026-05-10
source_path: raw/2290.pdf
url: https://pubmed.ncbi.nlm.nih.gov/9344352/
journal: Investigative Ophthalmology & Visual Science (IOVS)
volume: 38(11), 2290–2299
pages: 10
license: not specified (copyright Association for Research in Vision and Ophthalmology, 1997)
tags: [modality/ophthalmology, task/screening, task/classification, evaluation/external-validation, model-family/neural-network, historical]
---

# Current Keratoconus Detection Methods Compared With a Neural Network Approach (Smolek & Klyce 1997)

> The systematic validation paper that follows up the 1995 preliminary neural-network demonstration. Two independent networks: a **classification network** (KC / KCS / OTHER) and a **cone-severity network** (continuous 0.0–1.0 grading), each compared head-to-head against the contemporary keratoconus-detection methods on the same test set. The classification network achieves **100% accuracy, sensitivity, and specificity** on a 150-cornea test set across 9 corneal categories — significantly outperforming the Klyce/Maeda KCI (1994 expert system), the Rabinowitz K&I-S test, and average simulated keratometry. *Investigative Ophthalmology & Visual Science* 38(11):2290–2299, October 1997. Supported by NEI grants EY03311 and EY02377.

## Summary

This paper closes the [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) rung-three lineage with a rigorous, head-to-head comparison: the same group's own 1994 expert system (KCI) versus the same group's neural-network classifier from this paper, on the same test set, with full sensitivity/specificity/accuracy and McNemar's-test significance values.

**Dataset.** 300 TMS-1 (Tomey) videokeratoscope examinations, evenly split 150 train / 150 test, across **9 categories**: normal, with-the-rule astigmatism, keratoconus (KC1 mild, KC2 moderate, KC3 advanced), **keratoconus suspect (KCS)**, contact-lens-induced corneal warpage, pellucid marginal degeneration, photorefractive keratectomy, radial keratotomy, penetrating keratoplasty.

**Architecture.** Two independent networks (Brainmaker Professional v3.1):

| Network | Inputs | Hidden | Outputs |
|---|---|---|---|
| Classification | 10 indices | 55 neurons | 3 (KC, KCS, OTHER) |
| Cone severity | 10 indices | 34 neurons | 1 (continuous 0.0–1.0) |

Hidden-neuron count optimized empirically: 71 separate experiments per network varying hidden count from 5 to 75, selecting lowest mean training-set error. Inputs: DSI, OSI, CSI, AA, CYL, IAI, **SK1** (steep axis of simulated keratometry, new in this work as an explicit input), SRI, SAI, SDP.

**Results.**

- Classification network: **100% accuracy / 100% sensitivity / 100% specificity** on test set (150/150). KC sensitivity 100% (33/33), KCS sensitivity 100% (6/6).
- Cone-severity network: outputs cleanly separated across OTHER (0.02 ± 0.02), KCS (0.21 ± 0.05), KC1 (0.52 ± 0.17), KC2 (0.74 ± 0.12), KC3 (0.91 ± 0.15), differences between all five groups significant *p* < 0.001.
- Severity network correlates with the 1994 KPI baseline at *R* = 0.892, *p* < 0.0001 — but **distinguishes KC2 from KC3** and **distinguishes KCS from OTHER**, neither of which KPI alone can do.

**Comparison vs. contemporary methods (Tables 2–6):**

| Method | KC sens | KC spec | KCS sens | KCS spec | Total acc |
|---|---|---|---|---|---|
| **Classification network** | **100% (33/33)** | **100%** | **100% (6/6)** | **100%** | **100% (150/150)** |
| Rabinowitz K&I-S (TMS-2) | 100% (33/33) | 88.89% | 16.67% (1/6) | 91.67% | 80.67% |
| Klyce/Maeda KCI (1994 expert system) | 93.94% (31/33) | 93.16% | — (not detected) | — | 93.33% |
| Average Simulated Keratometry | 75.76% (25/33) | 80.34% | — | — | 79.33% |

McNemar's-test significance: classification network significantly better than every alternative on overall accuracy (*p* = 0.002 or less) and on specificity (*p* = 0.005 or less). On KC sensitivity alone, network and KCI are not significantly different — but the network's KCS detection (100% vs. Rabinowitz's 16.67%) is the decisive operational advantage.

## Key claims and findings

### The KCS problem this paper solves

**Keratoconus suspect (KCS)** is defined in this paper as *"corneas with a videokeratographic pattern of localized steepening but none of the traditional clinical signs of keratoconus, nor any other circumstances that might explain the topography pattern (e.g., trauma or contact lens wear)."* Pre-LASIK screening clinics in the mid-1990s were finding **5.7–10% of refractive-surgery candidates** exhibited KC or KC-like patterns. Distinguishing KCS from minor confounders (post-RK, post-PRK, contact-lens-induced warpage, pellucid marginal degeneration) is the clinically critical task — because surgery on a KCS eye can precipitate corneal ectasia.

The 1994 KCI expert system **does not even attempt to classify KCS** (KCS topographies should give a KCI value of 0%, but in practice often produce 20–36% likelihood-of-keratoconus outputs that confuse clinical reading). The Rabinowitz K&I-S method tries to detect KCS but achieves only 16.67% sensitivity, treating KCS as a milder form of KC rather than a distinct category. The classification network establishes a **dedicated KCS category** and trains the network end-to-end to discriminate it, achieving 100% sensitivity and specificity on the test set.

### Cone-severity network output thresholds

The severity-network output, calibrated against the discrete categories, yields the following operational thresholds:

- Output < 0.15 → OTHER (no keratoconus or suspect)
- 0.15 ≤ output < 0.30 → keratoconus suspect (KCS)
- 0.30 ≤ output ≤ 1.0 → keratoconus (continuous severity)

This is the **first objective, quantitative, numeric threshold for "keratoconus suspect" in the corneal-topography literature**, and it is generated by training a network rather than imposed by rules.

### Index importance analysis (Figure 4)

Retrospective sensitivity analysis ranks the inputs by their contribution to each network:

- **Classification network** (KC): SAI > CSI > OSI > SK1; same indices have opposite ranking (CSI > OSI > SAI > SK1) for KCS classification.
- **Cone-severity network**: OSI > CSI > SK1 > SAI > IAI > SDP have positive influence; SRI, DSI, CYL have negative influence; AA has no influence.

The DSI (Differential Sector Index, introduced in the 1994 paper to detect localized peripheral steepening) had only a minor influence — explained by lack of significant DSI difference between KC, KCS, pellucid marginal degeneration, and keratoplasty cases (Table 1). This is an honest negative finding the authors call out explicitly.

### Failure modes of KCI (1994 expert system) revealed

KCI had 8 false-positives for keratoconus on the test set. **Four of the eight were keratoconus suspects** (which KCI is not designed to classify but flags anyway), and **four were pellucid marginal degeneration cases**. The authors note: *"Apparently the expert rules of the KCI test tend to override the KPI result that correctly suggests that a keratoconus suspect is something other than true keratoconus."* This is a primary-source self-critique by the same group that built the 1994 KCI.

### Misclassification: none on the test set

For the classification network, the lowest correct output was 0.69 in the KC category; 144 of 150 maps had output ≥ 0.95. The remaining six maps had outputs in the 0.69–0.95 range but still cleanly above the 0.5 decision threshold. The network produced no incorrect responses on any test record.

## Why this paper matters

For this wiki:

1. **Validates rung-three with primary numbers.** Where [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) achieved 80% test accuracy on 75 maps as a "preliminary demonstration," this paper achieves 100% on 150 maps with a dedicated KCS category and head-to-head comparison against the prior expert system.
2. **Self-deprecating critique of the 1994 KCI.** The same group that built the 1994 expert system explicitly shows that their own neural network outperforms it on KCS detection and on overall specificity. This is unusually candid primary-source self-evaluation and informs the [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) lineage's transition narrative from rule-based to learned methods.
3. **Establishes the first objective KCS threshold.** "Keratoconus suspect" had been a subjective category before this paper; the severity-network thresholds (0.15 < KCS < 0.30) are statistically validated against expert classification.
4. **Direct commercial impact.** The classification + severity networks were embedded in the Tomey TMS-2 Keratoconus Screening Software as "KSI" (Klyce/Smolek Index, sometimes called the Smolek/Klyce Index). The 2006 CRST cover story ([klyce-mcdonald-slade-topographic-indices-2006](klyce-mcdonald-slade-topographic-indices-2006.md)) documents this KSI in clinical deployment 9 years later.
5. **Continuity of indices into modern deep learning.** Every keratoconus deep-learning paper from 2018 onward either uses these indices directly as inputs or compares against KPI/KCI/KSI baselines.

## Notes

- **Author order changed**: Smolek now first author (vs. Maeda/Klyce/Smolek on the 1994 and 1995 papers). Naoyuki Maeda had returned to Japan; Smolek (a research engineer at LSU Eye Center) drove the systematic-comparison study, with Klyce as senior author.
- **Implementation**: Brainmaker Professional v3.1 (one version after the 1995 paper). 71 separate training runs per network for hyperparameter search.
- **The dataset still excludes "atypical" maps** — focused on canonical patterns. This caveat from the 1995 paper persists.
- **Pellucid marginal degeneration (PMD)** is the most clinically important confounder for KC detection; the neural network distinguishes them correctly, while KPI tends to score some PMD cases in the keratoconus range (Figure 3B). This finding directly enables the post-2000 clinical practice of treating PMD vs. KC differently in refractive-surgery screening.
- **Direct citation chain**: this paper cites Maeda/Klyce/Smolek/Thompson 1994 (ref 30 — the [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) source) and Maeda/Klyce/Smolek 1995 (ref 33 — the [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) source) as the methodological precursors it directly extends.

## Entities and concepts touched

- [stephen-klyce](../entities/stephen-klyce.md) — senior author; concludes the rung-three lineage.
- [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) — rung 3 systematic validation.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — ophthalmology imaging-AI section.
- [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) — direct predecessor.
- [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) — rung-two predecessor whose KCI is benchmarked against here.
- [klyce-mcdonald-slade-topographic-indices-2006](klyce-mcdonald-slade-topographic-indices-2006.md) — 9-year-later commercial-deployment evidence; KSI (this paper's classification network) shipping in Tomey topographers.
- [clinical-validation](../concepts/clinical-validation.md) — 100% test-set accuracy on a controlled distribution; honest discussion of dataset-curation limits is a good early example of human-in-loop framing.
