---
type: source
title: Artificial Intelligence in Corneal Topography (Saleh & Hussein 2019)
authors: [Nazar Saleh, Nebras Hussein]
published: 2019
ingested: 2026-05-10
source_path: raw/10.38016-jista.456592-599649.pdf
url: https://dergipark.org.tr/en/pub/jista/issue/43287/599649
journal: Journal of Intelligent Systems Theory and Applications
volume: 2(1), 1–6
pages: 6
license: CC license (open access via DergiPark)
tags: [modality/ophthalmology, task/screening, task/classification, model-family/neural-network, model-family/svm, secondary-review]
---

# Artificial Intelligence in Corneal Topography (Saleh & Hussein 2019)

> A short (6-page) narrative review of machine-learning applications to corneal topography, organized by classifier family (ANN, SVM, decision tree, Naive Bayes, multi-classifier studies). Useful as a citation map for the late-1990s through mid-2010s corneal-topography ML literature; **methodologically light** and pre-dates the modern deep-learning wave. Saleh is at Aksaray University (Turkey); Hussein is at Khwarizmi College of Engineering, Baghdad, Iraq. *Journal of Intelligent Systems: Theory and Applications* 2(1):1–6, 2019.

## Summary

The paper surveys AI-based feature extraction and classification methods applied to corneal topography images, with a clinical framing around keratoconus and refractive-surgery screening. It groups the literature into five classifier categories — **artificial neural networks (ANN), support vector machines (SVM), decision trees (DT), Naive Bayes, and multi-classifier studies** — with brief paragraph summaries of each cited paper. The review concludes that all reviewed methods report high accuracy, sensitivity, and specificity for corneal-topography classification.

The ANN section opens with the [stephen-klyce](../entities/stephen-klyce.md) group's 1995 ([maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md)) and 1997 ([smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md)) papers as the seminal references, then jumps to de Carvalho & Barbosa 2008 (Zernike-coefficient inputs) and Kermany et al. 2018 (UC San Diego Cell paper on retinal-disease deep learning). The SVM section covers Netto 2005 (Hartmann-Shack-based framework), Bagherinia et al. 2008 (ATLAS 90000 topographer), Arbelaez et al. 2012 (Scheimpflug + Placido), Noaman et al. 2014 (SVM+ANN hybrid), and Ruiz Hidalgo et al. 2016 (Pentacam, 98.9% KC accuracy). The DT section covers Twa et al. 2005 (Zernike + C4.5 decision tree) and Kabari & Nwachukwu 2012 (hybrid ANN+DT). The Naive Bayes section is one paragraph (Kurniawan et al. 2014, 82% accuracy with case-based reasoning). Multi-classifier and survey work: Toutounchian et al. 2012, Zhang et al. 2014. Closes with a paragraph on Google DeepMind Health × Moorfields Eye Hospital (2016 announcement).

**The review does not engage with the post-2018 deep-learning wave in corneal topography** (Yousefi 2018 unsupervised ML, Kamiya 2019 AS-OCT deep learning, Pentacam-deep-learning systems from 2019 onward). Its temporal cutoff is effectively early 2018.

## Key claims and findings

### Klyce-group references receive prominence in the ANN section

The opening sentences of Section 2.1 (ANN-based classifiers) directly cite *Maeda, Klyce & Smolek (1995)* and *Smolek & Klyce (1997)* as the foundational work — confirming that two decades later, primary-source narrative reviews in this specialty treat the [stephen-klyce](../entities/stephen-klyce.md) group's 1995–97 neural-network papers as the anchor citations.

> "Some researchers, as early as 1995, attempted to evaluate the capabilities and usefulness of an automated system based on ANNs in interpreting the corneal topographic maps. … The study reported that the ANNs system may need further enhancements to be an objective computerized classification tool of video-keratography for helping the doctors in determining the abnormalities in corneal topographies (Maeda, Klyce, & Smolek, 1995)."
>
> "Smolek and Klyce (1997) conducted a study to compare four video-keratographic based keratoconus detection methods to a new detection method based on ANNs. … The research findings assured that the ANNs approach succeeded in differentiating between the topographies of the KC from KCS, and even from other cases that bear a resemblance to KC. … The ANNs method recorded a higher performance in terms of specificity and accuracy."

### Reported performance numbers from the cited literature

A useful aspect of this review is its tabulation of headline numbers from each cited study. Compiled here for the wiki's purposes:

| Year | Authors | Method | Task | Sens / Spec / Acc |
|---|---|---|---|---|
| 1995 | Maeda/Klyce/Smolek | ANN, 7 categories | corneal topography classification | 80% test accuracy ([primary](maeda-klyce-keratoconus-neural-network-1995.md)) |
| 1997 | Smolek/Klyce | ANN, 9 categories | KC + KCS detection | 100% across all three ([primary](smolek-klyce-keratoconus-detection-1997.md)) |
| 2005 | Twa et al. | Decision tree (C4.5) + Zernike | KC vs normal | 92% acc; AUC 0.97 |
| 2008 | Bagherinia et al. | SVM (ATLAS 90000) | KC + KCS + post-surgery vs normal | ≥ 90% across acc/sens/spec |
| 2012 | Arbelaez et al. | SVM (Placido + Scheimpflug) | KC + subclinical-KC + post-surgery + normal | 95% (with posterior surface data); 93% (without) |
| 2012 | Kabari & Nwachukwu | ANN+DT hybrid (NNDTEDDS) | myopia / hyperopia / astigmatism | 92% acc |
| 2012 | Toutounchian et al. | multi-classifier (DT, SVM, ANN, RBFNN, MLP) | KC + KCS + normal | 91% acc |
| 2014 | Noaman et al. | SVM+ANN | SPH / CYL detection | nonlinear-SVM specificity 92% → 97% with ANN |
| 2014 | Kurniawan et al. | Naive Bayes + CBR | eye disease diagnosis | 82% acc |
| 2016 | Ruiz Hidalgo et al. | SVM (Weka), 22 Pentacam parameters | KC vs normal | **98.9% acc / 99.1% sens / 98.5% spec** |
| 2016 | Ruiz Hidalgo et al. | SVM, 22 Pentacam parameters | forme fruste vs normal | 93.1% acc / 79.1% sens / 97.9% spec |

The numbers are consistent with the trajectory the wiki tracks elsewhere: classical-ML keratoconus detection plateaued at ~95–99% on controlled datasets through the early 2010s, before deep-learning systems entered the literature.

## Why this paper matters

For this wiki:

1. **Secondary citation map.** Useful as a single-page index into the 1995–2016 corneal-topography classical-ML literature for follow-up reading. Confirms the canonical citation status of the 1995 and 1997 Klyce-group neural-network papers in this specialty.
2. **Klyce-group primacy confirmed by an independent reviewer.** The review's structure places the 1995 Maeda/Klyce/Smolek and 1997 Smolek/Klyce papers as the foundational ANN references — independent third-party validation of the canonical-citation framing this wiki uses for [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md).
3. **Tabulates intermediate-era performance benchmarks.** The 1998–2016 classical-ML keratoconus detection literature reports 90–99% accuracy with hand-engineered features (Pentacam parameters, Zernike coefficients, KPI-family indices). These numbers contextualize the deep-learning literature's claims of further improvement.
4. **Documents the pre-deep-learning landscape that modern systems compare against.** The Pentacam-based 22-parameter SVM (Ruiz Hidalgo 2016) and the Scheimpflug + Placido SVM (Arbelaez 2012) are the recent baselines most modern KC-deep-learning papers benchmark against.

## Methodological caveats

The wiki should treat this paper as a **secondary reference**, not as primary evidence:

- Single-author group at one institution (Khwarizmi College of Engineering, Baghdad); not a systematic review (no PRISMA flow, no inclusion/exclusion criteria documented, no quality assessment).
- 6-page length is more accurately a "mini-review" or "tutorial overview."
- Several typos and grammatical issues (e.g., "SVM" misspelled as "SMV" in the section heading) suggest light editing.
- No primary data analysis or original meta-analysis.
- Temporal cutoff is early 2018 — does not engage with the post-2018 deep-learning wave (Yousefi unsupervised 2018, Kamiya AS-OCT 2019, modern Pentacam DL systems).
- Inconsistent referencing: cites the 1995 Klyce-group paper with date "1995" but also misattributes "as early as 1995" without acknowledging the 1994 expert-system paper that preceded it.

For primary citations on any specific 1995–2016 corneal-topography ML paper, prefer the underlying publication over this review.

## Notes

- **Affiliation discrepancy.** The corresponding author Saleh is listed as Aksaray University but with an `@yahoo.com` email; co-author Hussein at Khwarizmi College of Engineering, Baghdad, Iraq.
- **Journal context.** *Journal of Intelligent Systems: Theory and Applications* (JISTA) is a Turkish open-access AI/CS journal hosted on DergiPark. Not indexed in PubMed; not Web-of-Science-indexed at time of writing.
- **No conflict-of-interest statement** in the published PDF.
- **Citation precedence.** Where this paper and any of its cited primary sources both make a claim, **cite the primary**. This review is appropriate as the citation when summarizing the breadth of the 1995–2016 classical-ML corneal-topography landscape, but not as the authority for any individual technical claim.

## Entities and concepts touched

- [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) — secondary reference for the rung-three through rung-four transition period.
- [stephen-klyce](../entities/stephen-klyce.md) — third-party citation of Klyce-group papers as the foundational ANN work in corneal topography.
- [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) — cited as foundational ANN reference.
- [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md) — cited as the systematic-comparison ANN paper.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — ophthalmology imaging-AI context.
