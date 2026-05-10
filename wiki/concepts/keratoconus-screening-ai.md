---
type: concept
title: Keratoconus screening AI — from quantitative topography to deep learning
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/klyce-computer-assisted-corneal-topography-1984.md, ../sources/maeda-klyce-keratoconus-screening-1994.md, ../sources/ogut-ai-clinical-medicine-2025.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [modality/ophthalmology, task/screening, task/classification, historical]
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

Maeda, Klyce, Smolek, *Neural network classification of corneal topography: preliminary demonstration*, IOVS 36:1327–1335, 1995 ([PubMed 7775110](https://pubmed.ncbi.nlm.nih.gov/7775110/)). Multilayer perceptron trained on 11 topographic indices to classify into 7 categories (normal, with-the-rule astigmatism, keratoconus mild/moderate/advanced, post-PRK, post-keratoplasty). 100% training accuracy, 80% test accuracy (60/75 maps; per-category accuracy and specificity > 90%; sensitivity 44–100%).

Smolek & Klyce, *Current keratoconus detection methods compared with a neural network approach*, IOVS 38:2290–2299, 1997 ([PubMed 9344352](https://pubmed.ncbi.nlm.nih.gov/9344352/)). Systematic comparison: the neural network outperforms the contemporary alternatives (Rabinowitz–McDonnell I-S asymmetry, KISA% method, Keratoconus Severity Index (KSI)). Establishes the neural-network approach as the leading classification method for the field at the time.

Neither 1995 nor 1997 papers are yet in `raw/` for this wiki; they're cited here as the immediate methodological successors to the 1994 expert system.

### Rung 4 — Modern deep learning (2018–present)

The 2010s saw classical neural networks displaced by deep learning across imaging-AI broadly. For keratoconus specifically:

- **Yousefi et al. 2018** (PMC) — unsupervised machine learning for keratoconus classification.
- **Kamiya et al. 2019** (*BMJ Open Ophthalmology*) — deep-learning-based classifier on swept-source anterior-segment OCT.
- **Lozano-Castaneda et al. *Diagnostics* MDPI 2023** — systematic narrative review of keratoconus AI from fundamentals through deep learning. Treats the [klyce-computer-assisted-corneal-topography-1984](../sources/klyce-computer-assisted-corneal-topography-1984.md) and [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) papers as the foundational primary citations for the field. Modern deep-learning keratoconus papers routinely compare themselves against the KPI baseline.
- **Pentacam / Orbscan / Galilei / Sirius / Casia** — modern Scheimpflug and OCT-based videokeratographers ship with screening algorithms that draw on Klyce-group indices among others. NIDEK in particular has continuity with this lineage; Klyce is a current consultant.
- **EyeFM 2025** ([medical-imaging-ai](medical-imaging-ai.md), Wu/Dai et al. *Nature Medicine* Aug 2025): a multimodal foundation model for ophthalmology trained on 14.5M ocular images covering 5 imaging modalities. Not keratoconus-specific, but the closest 2025 analogue of "general-purpose ophthalmology AI" that the 1994 work pointed toward.

## Indices that survived from 1994

The 1994 paper's indices remain standard inputs to modern keratoconus-screening algorithms — both classical-ML and modern deep-learning systems include them as engineered features or compare against KPI baselines. The persistence of these specific quantities across 30+ years is unusual in clinical AI: most early-1990s engineered features have been displaced by learned representations.

| Index | Function | Still used? |
|---|---|---|
| KPI | Composite keratoconus likelihood | Yes — baseline for new methods |
| DSI | Localized peripheral steepening | Yes — clinical reading |
| OSI | Max opposite-sector power difference | Yes |
| CSI | Central steepening | Yes |
| SAI | Asymmetry of decentered cones | Yes |
| IAI | Inter-ring power irregularity | Yes |
| SimK1, SimK2 | Simulated keratometry | Standard topographic readout |
| KSI | Keratoconus Severity Index (Smolek/Klyce mid-1990s extension) | Yes |

The reason indices persist: they correspond to *biologically meaningful* topographic features clinicians already recognized. Deep-learning systems often outperform them numerically, but the indices remain interpretable handles for clinical reading.

## Why this lineage matters

For the wiki:

1. **Specialty-specific origin of imaging AI.** The three-rung pattern (quantitative imaging → expert system / classical ML → neural network / deep learning) that recurs across [medical-imaging-ai](medical-imaging-ai.md) has the [stephen-klyce](../entities/stephen-klyce.md) group as the primary investigator for all three rungs in corneal topography. Keratoconus AI is one of the longest continuous research programs in clinical AI.
2. **Parallel to other expert-system-era foundations.** The 1994 [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) work sits in the same expert-system wave as Pathfinder (1992; see [eric-horvitz](../entities/eric-horvitz.md)) and MYCIN (1976; cited in [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md)). The keratoconus screening problem is much more constrained than general diagnosis, which is why this expert system actually saw widespread clinical deployment — embedded in commercial videokeratographers shipped to ophthalmologists worldwide.
3. **Continuity of engineered features.** Most clinical-AI feature engineering has been displaced by deep learning, but the KPI/DSI/OSI/CSI/SAI/IAI indices remain in routine use 30 years later. They are an existence proof that well-chosen biologically-grounded features can outlast their original classifiers.
4. **Pre-FDA-clearance precedent.** The 1994 expert system was deployed via TMS-1 software updates to ophthalmology clinics globally without formal FDA-clearance treatment as a "medical device" — videokeratoscopes themselves were the regulated artifact. By contrast, modern AI-based keratoconus detectors must go through the [fda-510k-pathway](fda-510k-pathway.md). The regulatory framework has evolved around what was once "just software in a topography machine."

## Cross-references

- [stephen-klyce](../entities/stephen-klyce.md) — principal investigator across rungs 1–3.
- [medical-imaging-ai](medical-imaging-ai.md) — broader specialty-AI imaging context.
- [eric-horvitz](../entities/eric-horvitz.md) — parallel expert-system-era figure in general diagnostic AI.
- [agentic-clinical-ai](agentic-clinical-ai.md) — modern multi-agent / rule-based architecture lineage descends from 1990s expert-system work.
- [clinical-validation](clinical-validation.md) — the 1994 paper explicitly positions the system as screening + clinician confirmation, an early articulation of the human-in-loop framing the wiki centers.

## Open / to-ingest

- Maeda, Klyce, Smolek 1995 IOVS — neural-network preliminary demonstration ([PubMed 7775110](https://pubmed.ncbi.nlm.nih.gov/7775110/)).
- Smolek & Klyce 1997 IOVS — neural-network systematic comparison ([PubMed 9344352](https://pubmed.ncbi.nlm.nih.gov/9344352/)).
- Lozano-Castaneda et al. 2023 *Diagnostics* MDPI — systematic narrative review.
- Yousefi et al. 2018 unsupervised keratoconus ML — primary citation.
- Kamiya et al. 2019 deep-learning keratoconus on swept-source AS-OCT.
- Modern Scheimpflug / OCT deep-learning keratoconus comparison studies.

## Sources

- [klyce-computer-assisted-corneal-topography-1984](../sources/klyce-computer-assisted-corneal-topography-1984.md) — rung-one primary.
- [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) — rung-two primary.
- [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md) — secondary reference for MYCIN era context.
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) — secondary reference for 2025 ophthalmology-AI state-of-the-art (EyeFM, DeepRETStroke, DeepDKD).
