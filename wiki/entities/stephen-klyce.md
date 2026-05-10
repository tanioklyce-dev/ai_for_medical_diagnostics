---
type: entity
title: Stephen D. Klyce, PhD, FARVO
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/klyce-computer-assisted-corneal-topography-1984.md, ../sources/maeda-klyce-keratoconus-screening-1994.md]
tags: [person, modality/ophthalmology, organization/lsu, organization/mount-sinai, organization/stanford, task/screening, task/classification]
---

# Stephen D. Klyce, PhD, FARVO

A vision-research physiologist whose career laid the **quantitative-imaging and pattern-classification foundation** that modern ophthalmology AI sits on. Klyce's group at the LSU Eye Center authored the first widely adopted computer-assisted corneal topography system (1984) and the first explicitly-AI-labeled (expert-system) classifier for keratoconus screening from videokeratography (1994), then extended that work to **the first neural-network corneal-topography classifier** (1995). His co-developed indices and decision-tree machinery are still cited in current keratoconus AI papers four decades later.

## Career

| Period | Role |
|---|---|
| 1971 | PhD, Physiology (vision research), Yale University |
| 1972–1979 | Stanford University, ophthalmology research |
| 1979–2008 | LSU School of Medicine, New Orleans — Professor of Ophthalmology and Anatomy/Cell Biology. Adjunct Professor of Biomedical Engineering, Tulane University. LSU Eye Center / Lions Eye Research Laboratories. |
| 2008–present | Adjunct Professor of Ophthalmology, Icahn School of Medicine at Mount Sinai (New York) |

**~250 peer-reviewed publications and book chapters.** Editorial board service on multiple ophthalmology and refractive-surgery journals. Industry consulting roles for NIDEK Inc., Smart EyeDeas, and Oculus (commercial corneal-imaging technology vendors).

## Selected awards

- **1990** CLAO Everett Kinsey Lecture
- **1991** ISRS Lans Distinguished Lecturer in Refractive Surgery
- **1991** American Academy of Optometry Max Schapiro Memorial Lecture
- **1996** American Academy of Ophthalmology Whitney Sampson Lecture
- **2000** American Society for Cataract and Refractive Surgery (ASCRS) Innovator Award
- **2003** International Society for Contact Lens Research Ruben Medal
- **2007** ISRS / AAO Casebeer Lecture Award
- **2008** Italian Refractive Surgery Society Research and Innovation Award
- **2009** Association for Research in Vision and Ophthalmology (ARVO) **Gold Fellow** Award (the basis for the FARVO postnominal)
- **2010** ISRS / AAO Barraquer Award
- **2016** *Journal of Refractive Surgery* Waring Medal for Editorial Excellence

## Contributions to medical AI

Klyce's AI-relevant work follows the same three-rung ladder that recurs across [medical-imaging-ai](../concepts/medical-imaging-ai.md): **quantitative imaging → statistical/expert-system classification → neural networks → deep learning.** He was a primary investigator on the first three rungs specifically for corneal topography.

### Rung 1 — Computer-assisted quantitative corneal topography (1984)

*Klyce SD. Computer-assisted corneal topography: high-resolution graphic presentation and analysis of keratoscopy. **IOVS** 25:1426–1435, 1984.* See [klyce-computer-assisted-corneal-topography-1984](../sources/klyce-computer-assisted-corneal-topography-1984.md).

A working corneal-topography system on a PDP 11/34A minicomputer running UNIX, written in C, with five modules (`digitize`, `smooth`, `kap`, `draw`, `complot`). 7,000 points / 180 meridians / 9 corneal rings per photograph. Calibration correlation 0.998 vs reference radius gauge. **The first widely-cited demonstration that corneal shape could be quantitatively characterized and visualized in 3D from keratoscope photographs**, moving the field from subjective visual inspection of mire ring patterns toward objective measurement.

The paper's most notable forward-looking passage:

> "Early in the course of this project, two additional computer programs were planned. One named *diagnose* was to have looked at the data for shape anomalies such as keratoconus and astigmatism. The second, named *learn*, was to have maintained a data base containing patient histories, physician diagnoses, and diagnoses provided by *diagnose*. **Such an expert system is within the realm of current technology.**"

In December 1984, Klyce sketched the architecture for both an automated diagnostic classifier *and* a continuously-learning patient + AI diagnosis database — the closed-loop concept that today's continuous-learning EHR-AI feedback systems instantiate. He deferred building them because manual inspection of his graphical output was already accurate; his group returned to the diagnostic-classifier part ten years later.

### Rung 2 — Expert-system keratoconus classification (1994)

*Maeda N, Klyce SD, Smolek MK, Thompson HW. Automated keratoconus screening with corneal topography analysis. **IOVS** 35:2749–2757, 1994.* See [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md).

200-cornea study, 8 topographic indices (5 newly developed in this work — **DSI, OSI, CSI, IAI, AA** — plus the preexisting SimK1, SimK2, SAI), processed by **linear discriminant analysis** (SAS 6.06) into a composite **Keratoconus Prediction Index (KPI)**. KPI is then embedded in a **rule-based expert system** (Pascal binary decision tree) that distinguishes peripheral keratoconus, central keratoconus, borderline, and non-keratoconus from confounders (post-keratoplasty, photorefractive keratectomy, contact lens-induced warpage, etc.).

- Validation set: **89% sensitivity, 99% specificity, 96% accuracy.**
- Expert system significantly outperformed discriminant analysis alone (68% → 89% sensitivity; McNemar *p* = 0.016).
- Explicitly labeled in the paper as AI: *"An expert system is an artificial intelligence approach that contains a modifiable knowledge base (rules and facts), an interface to users, and an interface engine that makes logic-based decisions."*

This places Klyce's work alongside [eric-horvitz](eric-horvitz.md)'s Pathfinder (1992) and Buchanan/Shortliffe's MYCIN (1976) in the **expert-system era of medical AI** — but specifically for ophthalmology, in the same year ([medical-imaging-ai](../concepts/medical-imaging-ai.md) modern ophthalmology AI directly descends from this lineage).

### Rung 3 — Neural-network corneal-topography classification (1995–1997)

*Maeda N, Klyce SD, Smolek MK. Neural network classification of corneal topography: preliminary demonstration. **IOVS** 36:1327–1335, 1995.* (PubMed 7775110; not yet ingested into `raw/`.)

The group's first application of a multi-layer perceptron neural network to corneal-topography classification. **11 topography-characterizing indices** from the TMS-1 videokeratoscope, paired with diagnostic category labels, used to train the network across **7 categories**: normal, with-the-rule astigmatism, keratoconus (mild, moderate, advanced), post-photorefractive keratectomy, post-keratoplasty.

- 183 maps total; 108 training / 75 test.
- 100% training accuracy; 80% test accuracy (60/75 correct).
- Per-category accuracy and specificity > 90%; sensitivity 44–100%.

*Smolek MK, Klyce SD. Current keratoconus detection methods compared with a neural network approach. **IOVS** 38:2290–2299, 1997.* (PubMed 9344352; not yet ingested.) The follow-up systematic comparison of contemporary keratoconus-detection methods to the neural-network classifier. **Establishes the neural-network approach as the leading detection method** for the field at the time.

### Subsequent influence

Klyce's KPI, DSI, OSI, CSI, IAI, and SAI indices remain standard inputs to keratoconus-screening algorithms today, including modern deep-learning systems. Reviews of the AI-in-keratoconus literature (e.g., the systematic narrative review by Lozano-Castaneda et al., *Diagnostics* MDPI 2023) treat his 1994 / 1995 work as the foundational primary citations for the field; modern keratoconus deep-learning papers compare themselves against the KPI baseline. See [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) for the full lineage.

The current **TMS-1 / TMS-4 / Pentacam / Orbscan** videokeratoscope ecosystem (NIDEK, Oculus, Bausch & Lomb) ships with screening algorithms that descend from Klyce-group indices, and Klyce has consulted for NIDEK and Oculus directly.

## Position in the broader medical-AI history

Klyce occupies a **specialty-specific** parallel to several connecting figures the wiki tracks elsewhere:

- [eric-horvitz](eric-horvitz.md) — Bayesian-decision-theory diagnostic-AI lineage (Pathfinder 1992 → MAI-DxO 2025). Horvitz worked the general-diagnosis problem; Klyce worked corneal-topography classification. Both span expert-system → modern eras with continuous publication.
- The MYCIN authors (Buchanan, Shortliffe 1976; cited in [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md) as a foundational rule-based clinical expert system) — same era, different specialty.
- More recent ophthalmology-AI work (Gulshan et al. 2016 diabetic retinopathy, EyeFM 2025, DeepRETStroke 2025, DeepDKD 2025) — direct descendants of the imaging-AI program Klyce helped initiate.

## Open / follow-up

- Smolek & Klyce 1997 (PubMed 9344352) and Maeda/Klyce/Smolek 1995 (PubMed 7775110) are not yet in `raw/`. Both would close the lineage from rule-based expert system → neural network in this group's work.
- A direct comparison of KPI-era indices against modern deep-learning keratoconus classifiers (Yousefi 2018 onward) would be a useful wiki page if/when the literature gets ingested.
- Whether the TMS-1's screening algorithms shipped from Computed Anatomy / NIDEK trace specifically to Klyce-group code is plausible but not directly cited in the papers we have; would need a primary source to claim.

## Sources

- [klyce-computer-assisted-corneal-topography-1984](../sources/klyce-computer-assisted-corneal-topography-1984.md) (raw/1426.pdf — 1984 IOVS, primary)
- [maeda-klyce-keratoconus-screening-1994](../sources/maeda-klyce-keratoconus-screening-1994.md) (raw/2749.pdf — 1994 IOVS, primary)
- [Stephen D. Klyce, PhD, FARVO — speaker profile (International Vision Optics)](http://www.ivo.gr/en/summerschool/organizing/klyce.html) — biographical / career details and awards list
- [Mount Sinai faculty profile, Stephen D Klyce](https://profiles.mountsinai.org/stephen-d-klyce)
- [Optical Express IMAB profile, Dr. Stephen Klyce](https://www.opticalexpress.co.uk/about/imab/stephen-klyce)
- Maeda, Klyce, Smolek 1995, *Neural network classification of corneal topography: preliminary demonstration*, IOVS — [PubMed 7775110](https://pubmed.ncbi.nlm.nih.gov/7775110/) (cited; not in `raw/`)
- Smolek & Klyce 1997, *Current keratoconus detection methods compared with a neural network approach*, IOVS — [PubMed 9344352](https://pubmed.ncbi.nlm.nih.gov/9344352/) (cited; not in `raw/`)
