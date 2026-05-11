---
type: concept
title: Keratoconus screening AI — from quantitative topography to deep learning
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/klyce-computer-assisted-corneal-topography-1984.md, ../sources/maeda-klyce-keratoconus-screening-1994.md, ../sources/maeda-klyce-keratoconus-neural-network-1995.md, ../sources/smolek-klyce-keratoconus-detection-1997.md, ../sources/klyce-mcdonald-slade-topographic-indices-2006.md, ../sources/saleh-hussein-ai-corneal-topography-2019.md, ../sources/ogut-ai-clinical-medicine-2025.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [modality/ophthalmology, task/screening, task/classification, historical, deployment]
---

# Keratoconus screening AI

A four-decade lineage of automated corneal-shape classification, beginning with manual digitization on a PDP 11/34A in 1984 and continuing into 2025 deep-learning systems. **Keratoconus** is a non-inflammatory progressive corneal-thinning disorder; early detection is clinically important because it changes contact-lens fitting, contraindicates LASIK and other refractive surgery, and benefits from prompt cross-linking therapy if available. Quantitative topographic AI screening has been the standard pre-refractive-surgery workup for two decades, and the underlying indices were largely developed by the [stephen-klyce](../entities/stephen-klyce.md) group at LSU in the 1990s.

## The four rungs of the lineage

### Rung 1 — Quantitative topography (1984)

[Klyce 1984](../sources/klyce-computer-assisted-corneal-topography-1984.md). First widely cited demonstration that corneal shape can be reconstructed quantitatively in 3D from keratoscope photographs. Manual digitization (~10 min/photo) → C-language smoothing + spherical projection → stereoscopic surface rendering plus difference plots. Not AI; not yet automated diagnosis. The classification step was *planned* (Klyce's never-built `diagnose` module) but visual inspection of the graphical output was already accurate enough for clinical use.

### Rung 2 — Expert-system + discriminant analysis (1994)

[Maeda, Klyce, Smolek, Thompson 1994](../sources/maeda-klyce-keratoconus-screening-1994.md). The first explicitly-AI-labeled keratoconus screening system. Eight topographic indices (DSI, OSI, CSI, IAI, AA — all newly developed in this work — plus SimK1, SimK2, SAI) fed into linear discriminant analysis to produce a composite **Keratoconus Prediction Index (KPI)**. KPI then embedded in a rule-based binary decision tree (Pascal) that classifies non-keratoconus / borderline / peripheral-keratoconus / central-keratoconus and rejects key confounders (post-keratoplasty, photorefractive keratectomy, contact-lens-induced warpage).

**Validation set: 89% sensitivity, 99% specificity, 96% accuracy.** Statistically significant gain over discriminant analysis alone (68% sens → 89% sens; McNemar *p* = 0.016).

### Rung 3 — Neural network classification (1995–1997)

[Maeda, Klyce, Smolek 1995](../sources/maeda-klyce-keratoconus-neural-network-1995.md). Self-described as *"to our knowledge, the first report of the successful application of a neural network model to classify corneal topography."* 3-layer backpropagation network (11 inputs → 18 hidden neurons → 7 output categories), trained on 11 topographic indices (the 1994 KPI-family indices + the new SDP index) to classify into 7 categories (normal, with-the-rule astigmatism, keratoconus mild/moderate/advanced, post-PRK, post-keratoplasty). 183 maps, 108 train / 75 test. 100% training accuracy, **80% test accuracy** (60/75 maps; per-category accuracy and specificity > 90%; sensitivity 44–100%). Implementation: Brainmaker Professional v2.53 on an 80486 PC. The authors explicitly acknowledge overfitting (training 100% vs. test 80%, χ² *p* = 0.0001) and frame the result as a **preliminary demonstration**.

[Smolek & Klyce 1997](../sources/smolek-klyce-keratoconus-detection-1997.md). Systematic head-to-head comparison: two independent networks (classification + cone-severity) on 150 train / 150 test corneas across **9 categories** (now including a dedicated keratoconus-suspect category). **Classification network: 100% accuracy, sensitivity, and specificity on test set.** Significantly outperforms the 1994 Klyce/Maeda KCI (93.94% KC sensitivity, 93.33% total accuracy), the Rabinowitz K&I-S test (80.67% total accuracy), and average simulated keratometry (79.33%). Establishes the **first objective quantitative threshold for "keratoconus suspect" (KCS)** — a category the 1994 expert system could not handle. This network shipped as **KSI (Klyce/Smolek Index)** in commercial Tomey topographers.

### Rung 3.5 — Commercial deployment by 2006

[Klyce, McDonald, Slade 2006 CRST](../sources/klyce-mcdonald-slade-topographic-indices-2006.md). By 2006, the rung-2 and rung-3 work was running in **three competing commercial videokeratographers** used in clinical refractive-surgery practice:

| System | AI machinery |
|---|---|
| Tomey Keratoconus Screening Software | KCI (1994 expert system) + KSI (1997 neural network) running side-by-side |
| Humphrey/Zeiss Pathfinder | CIM, Shape Factor, Mean Toric K — color-coded population-threshold display |
| **Nidek Corneal Navigator** | **Deployed neural-network classifier** across 7 categories incl. keratoconus suspect, pellucid marginal degeneration, post-keratoplasty, myopic/hyperopic refractive surgery |

The Nidek Corneal Navigator is **a deployed clinical neural-network classifier in 2006** — twelve years before the deep-learning wave broke into mainstream medical imaging. Klyce's paid-consultant role at Nidek (documented in the 2006 paper) is the direct research-to-industry pipeline. This commercial-deployment evidence corrects a common framing that "clinical AI" began with Gulshan/Esteva 2016–17 deep-learning papers.

### Rung 4 — Modern deep learning (2018–present)

The 2010s saw classical neural networks displaced by deep learning across imaging-AI broadly. For keratoconus specifically:

- **Intermediate-era classical ML** — by 2008–16, SVM-based Pentacam classifiers were achieving 93–99% accuracy on KC vs normal (Bagherinia 2008, Arbelaez 2012, Ruiz Hidalgo 2016) using the same KPI-family indices as inputs. See [saleh-hussein-ai-corneal-topography-2019](../sources/saleh-hussein-ai-corneal-topography-2019.md) for a survey of this transitional era.
- **Yousefi et al. 2018** (PMC) — unsupervised machine learning for keratoconus classification.
- **Kamiya et al. 2019** (*BMJ Open Ophthalmology*) — deep-learning-based classifier on swept-source anterior-segment OCT.
- **Lozano-Castaneda et al. *Diagnostics* MDPI 2023** — systematic narrative review of keratoconus AI from fundamentals through deep learning. Treats the [klyce-computer-assisted-corneal-topography-1984](../sources/klyce-computer-assisted-corneal-topography-1984.md) and [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) papers as the foundational primary citations for the field. Modern deep-learning keratoconus papers routinely compare themselves against the KPI baseline.
- **Pentacam / Orbscan / Galilei / Sirius / Casia** — modern Scheimpflug and OCT-based videokeratographers ship with screening algorithms that draw on Klyce-group indices among others. Nidek in particular has continuity with this lineage; Klyce was the original Corneal Navigator consultant ([2006 CRST](../sources/klyce-mcdonald-slade-topographic-indices-2006.md)).
- **EyeFM 2025** ([medical-imaging-ai](medical-imaging-ai.md), Wu/Dai et al. *Nature Medicine* Aug 2025): a multimodal foundation model for ophthalmology trained on 14.5M ocular images covering 5 imaging modalities. Not keratoconus-specific, but the closest 2025 analogue of "general-purpose ophthalmology AI" that the 1994 work pointed toward.

## Indices that survived from 1994–1997

The 1994/1995/1997 papers' indices remain standard inputs to modern keratoconus-screening algorithms — both classical-ML and modern deep-learning systems include them as engineered features or compare against KPI baselines. The persistence of these specific quantities across 30+ years is unusual in clinical AI: most early-1990s engineered features have been displaced by learned representations.

| Index | Function | Originated | Still used? |
|---|---|---|---|
| KPI (Keratoconus Prediction Index) | Composite keratoconus likelihood | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes — baseline for new methods |
| KCI (Klyce/Maeda Keratoconus Index) | Expert-system likelihood (0–100%) | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes — Tomey commercial |
| KSI (Klyce/Smolek Keratoconus Severity Index) | NN-based severity (0.0–1.0) with objective KCS threshold | [1997](../sources/smolek-klyce-keratoconus-detection-1997.md) | Yes — Tomey commercial |
| DSI (Differential Sector Index) | Localized peripheral steepening | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes — clinical reading |
| OSI (Opposite Sector Index) | Max opposite-sector power difference | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes |
| CSI (Center/Surround Index) | Central steepening | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes |
| SAI (Surface Asymmetry Index) | Asymmetry of decentered cones | pre-1994 (Klyce group) | Yes |
| IAI (Irregular Astigmatism Index) | Inter-ring power irregularity | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes |
| AA (Analyzed Area) | Data completeness | [1994](../sources/maeda-klyce-keratoconus-screening-1994.md) | Yes |
| SDP (Standard Deviation of Power) | Variance in area-corrected corneal power | [1995](../sources/maeda-klyce-keratoconus-neural-network-1995.md) | Yes |
| SimK1, SimK2 | Simulated keratometry | pre-1994 (Klyce group) | Standard topographic readout |

The reason indices persist: they correspond to *biologically meaningful* topographic features clinicians already recognized. Deep-learning systems often outperform them numerically, but the indices remain interpretable handles for clinical reading.

## Why this lineage matters

For the wiki:

1. **Specialty-specific origin of imaging AI.** The four-rung pattern (quantitative imaging → expert system → neural network → deep learning) that recurs across [medical-imaging-ai](medical-imaging-ai.md) has the [stephen-klyce](../entities/stephen-klyce.md) group as the primary investigator for the first three rungs in corneal topography. Keratoconus AI is one of the longest continuous research programs in clinical AI.
2. **Parallel to other expert-system-era foundations.** The 1994 [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) work sits in the same expert-system wave as Pathfinder (1992; see [eric-horvitz](../entities/eric-horvitz.md)) and MYCIN (1976; cited in [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md)). The keratoconus screening problem is much more constrained than general diagnosis, which is why this expert system actually saw widespread clinical deployment — embedded in commercial videokeratographers shipped to ophthalmologists worldwide.
3. **Continuity of engineered features.** Most clinical-AI feature engineering has been displaced by deep learning, but the KPI/DSI/OSI/CSI/SAI/IAI/AA/SDP indices remain in routine use 30 years later. They are an existence proof that well-chosen biologically-grounded features can outlast their original classifiers.
4. **Pre-FDA-clearance precedent.** The 1994 expert system and 1997 neural network were deployed via Tomey, Humphrey/Zeiss, and Nidek software updates to ophthalmology clinics globally **by 2006** ([klyce-mcdonald-slade-topographic-indices-2006](../sources/klyce-mcdonald-slade-topographic-indices-2006.md)) without formal FDA-clearance treatment as separate AI "medical devices" — videokeratoscopes themselves were the regulated artifact. By contrast, modern AI-based keratoconus detectors must go through the [fda-510k-pathway](fda-510k-pathway.md). The regulatory framework has evolved around what was once "just software in a topography machine."
5. **Fast research-to-deployment.** The general clinical-AI framing in [clinical-validation](clinical-validation.md) emphasizes how slowly research translates to clinical deployment. This lineage **does not fit that framing**: the 1994 KCI was in commercial Tomey software within ~5 years; the 1997 KSI within ~9 years; the Nidek Corneal Navigator neural-network classifier was deployed clinically by ~2005, eight years after [smolek-klyce-keratoconus-detection-1997](../sources/smolek-klyce-keratoconus-detection-1997.md). The likely reason: Klyce's direct industry-consulting role across Tomey, Nidek, and others, plus the constrained classification problem (10 well-defined corneal categories) versus general diagnosis.
6. **Human-in-loop framing is 20 years old.** [klyce-mcdonald-slade-topographic-indices-2006](../sources/klyce-mcdonald-slade-topographic-indices-2006.md) explicitly frames the AI indices as screening-aids-not-diagnostics: *"None is 100% specific, sensitive, or accurate. Practitioners must interpret the diagnostic information … within the context of all the available clinical information."* The same framing is the 2025–26 ARISE / FURM / FDA-510k consensus. The 2006 Klyce-group articulation predates the modern formulation by two decades.

## Cross-references

- [stephen-klyce](../entities/stephen-klyce.md) — principal investigator across rungs 1–3.
- [medical-imaging-ai](medical-imaging-ai.md) — broader specialty-AI imaging context.
- [eric-horvitz](../entities/eric-horvitz.md) — parallel expert-system-era figure in general diagnostic AI.
- [agentic-clinical-ai](agentic-clinical-ai.md) — modern multi-agent / rule-based architecture lineage descends from 1990s expert-system work.
- [clinical-validation](clinical-validation.md) — the 1994 paper explicitly positions the system as screening + clinician confirmation, an early articulation of the human-in-loop framing the wiki centers.

## Open / to-ingest

- Lozano-Castaneda et al. 2023 *Diagnostics* MDPI — systematic narrative review.
- Yousefi et al. 2018 unsupervised keratoconus ML — primary citation.
- Kamiya et al. 2019 deep-learning keratoconus on swept-source AS-OCT.
- Modern Scheimpflug / OCT deep-learning keratoconus comparison studies.
- Klyce/Karon/Smolek 2005 *J Refract Surg* 21(suppl):617–22 — primary description of the Nidek Corneal Navigator deployed neural-network classifier.

## Sources

- [klyce-computer-assisted-corneal-topography-1984](../sources/klyce-computer-assisted-corneal-topography-1984.md) — rung-1 primary.
- [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) — rung-2 primary.
- [maeda-klyce-keratoconus-neural-network-1995](../sources/maeda-klyce-keratoconus-neural-network-1995.md) — rung-3a primary.
- [smolek-klyce-keratoconus-detection-1997](../sources/smolek-klyce-keratoconus-detection-1997.md) — rung-3b primary (systematic validation).
- [klyce-mcdonald-slade-topographic-indices-2006](../sources/klyce-mcdonald-slade-topographic-indices-2006.md) — commercial-deployment primary; documents Tomey/Humphrey/Nidek deployment in 2006.
- [saleh-hussein-ai-corneal-topography-2019](../sources/saleh-hussein-ai-corneal-topography-2019.md) — secondary reference for the intermediate (2000s–2010s) classical-ML era.
- [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md) — secondary reference for MYCIN-era context.
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) — secondary reference for 2025 ophthalmology-AI state-of-the-art (EyeFM, DeepRETStroke, DeepDKD).
