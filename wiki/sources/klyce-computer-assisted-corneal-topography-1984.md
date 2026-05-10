---
type: source
title: Computer-Assisted Corneal Topography — High-Resolution Graphic Presentation and Analysis of Keratoscopy (Klyce 1984)
authors: [Stephen D. Klyce]
published: 1984-12
ingested: 2026-05-10
source_path: raw/1426.pdf
journal: Investigative Ophthalmology & Visual Science (IOVS)
volume: 25(12), 1426–1435
pages: 10
license: not specified (copyright Association for Research in Vision and Ophthalmology, 1984)
tags: [modality/ophthalmology, task/segmentation, task/classification, historical, evaluation/external-validation]
---

# Computer-Assisted Corneal Topography (Klyce 1984)

> The first widely-cited demonstration of **quantitative computer-based corneal topography**. Sole author: [Stephen D. Klyce](../entities/stephen-klyce.md), then at the Lions Eye Research Laboratories, LSU Eye Center, Louisiana State University Medical Center School of Medicine, New Orleans. Funded by PHS grants EY03311 and EY02377 and the Louisiana Lions Eye Foundation. Submitted November 8, 1983; published December 1984 in *Investigative Ophthalmology & Visual Science* 25:1426–1435. Presented in part at the 1984 ARVO Annual Meeting (Sarasota).

## Summary

Klyce describes a five-module C-language system on a PDP 11/34A minicomputer (Digital Equipment Corp), running UNIX (courtesy of Bell Labs), that converts photographs from a **Sun Contact Lens Co. Photo-keratoscope** (Kyoto) into a quantitative three-dimensional reconstruction of the corneal surface. The system handles ~7,000 manually-digitized data points per photograph and supports analysis along up to 180 corneal meridians across 9 concentric corneal rings, producing both tabular surface-power readings (in diopters) and **stereoscopic 3D rendering** of corneal shape — including "difference plots" that amplify deviations from a perfect sphere to highlight clinical anomalies.

Calibration against six Lucite hemispheres of known radii (6.9–8.4 mm) demonstrated a linear-regression correlation of **0.998** (*p* < 0.001) between calculated and measured radii, with measured standard deviations smaller than 50 µm. Three patient demonstrations follow: a normal emmetropic eye, a diagnosed keratoconus cornea, and a case of **post-keratoplasty severe regular astigmatism that was actually keratoconic** — quantitative analysis correctly characterized the saddle-on-cone shape that visual inspection of the original mires had missed. This is the paper's clinical-utility argument: the eye-and-brain of an expert can recognize the standard mire-pattern anomalies (keratoconus, astigmatism), but subtle distortions, induced astigmatism, and post-surgical irregularities are difficult to evaluate without quantitative output.

The system was conceived as a research tool but built with diagnostic intent. The closing paragraphs explicitly map a future expert-system architecture: an automatic-detection module (`diagnose`) and a continuously-learning patient + AI diagnosis database (`learn`). Klyce notes those modules were deferred not for technical reasons but because manual inspection of his graphical output was already accurate; he labels their construction as "within the realm of current technology." This vision predates his group's first AI-labeled clinical implementation by exactly 10 years (see [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md)).

## Key claims and findings

### System architecture (Appendix, Table A1)

Five C-language program modules, each ≤64 KB compiled (PDP 11/34A constraint):

| Module | Function |
|---|---|
| `digitize` | Stores demographic data; accepts manual coordinate entry from a graphics digitizing tablet (Houston Ins. Model DT-11; ~10 min per photograph for a trained operator); converts rectangular → polar coordinates; eliminates static-induced "wild" coordinates. |
| `smooth` | Linearly interpolates missing coordinates; performs geometric averaging every 2° of arc; applies cyclized least-squares 7-point polynomial fit; refines innermost-ring geometric-center estimate. |
| `kap` (Keratoscope Analysis Program) | Converts smoothed 2D polar data → three-dimensional corneal surface; outputs surface elevation and refractive power at incremental positions; generates summary report of corneal dimensions. |
| `draw` | Three-dimensional rendering with rotation, perspective, and space transforms; produces stereoscopic surface views and stereoscopic difference plots vs. a perfect sphere. |
| `complot` | Drives an incremental hardware plotter for output. |

### Calibration (Figure 1)

Six precision Lucite hemispheres (6.9–8.4 mm radii) photographed and processed through the full pipeline. Results: standard deviations < 50 µm; linear regression slope 1.007 ± 0.025; intercept 0.036 ± 0.032; correlation 0.998 (*p* < 0.001). Outer ring images analyzable without finding systematic errors. Overall measurement error < 100 µm.

### Patient demonstrations

- **Normal emmetropic eye (Figure 3)**: difference plot shows only mild peripheral flattening — consistent with the lens-aberration literature.
- **Keratoconus cornea (Figure 4)**: conical deviation clearly illustrated in the difference plot. Quantitative validation of keratoconus diagnosis without needing slit-lamp confirmation.
- **Post-keratoplasty severe regular astigmatism initially diagnosed as standard astigmatism (Figure 6)**: stereoscopic and difference-plot output reveals a saddle-on-cone — keratoconus underlying the astigmatism. *"Initial diagnosis missed."* This single case study makes the paper's clinical-utility argument concretely.

### The explicit expert-system vision (Discussion, p. 1435)

The paper's penultimate paragraph:

> *"Early in the course of this project, two additional computer programs were planned. One named **diagnose** was to have looked at the data for shape anomalies such as keratoconus and astigmatism. The second, named **learn**, was to have maintained a data base containing patient histories, physician diagnoses, and diagnoses provided by **diagnose**. **Such an expert system is within the realm of current technology.** However, these two components were set aside when it became clear that accurate diagnoses were easily made by inspection of the graphic and tabular presentations."*

This is the architectural sketch of an automated diagnostic classifier paired with a continuously-learning patient + AI diagnosis database — both written in December 1984. The 1994 [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) paper realizes the `diagnose` component as a discriminant-analysis + rule-based expert system.

## Why this paper matters

For this wiki, three reasons:

1. **Quantitative-imaging foundation.** Modern ophthalmology-AI models (EyeFM, DeepRETStroke, DeepDKD; see [medical-imaging-ai](../concepts/medical-imaging-ai.md)) presume digital quantitative measurement of the cornea / retina. Klyce 1984 is the first widely-cited demonstration that this is feasible for corneal shape — moving the field from subjective interpretation of mire patterns toward objective surface measurement.

2. **Pre-AI medical-AI vision.** The "*expert system within the realm of current technology*" passage is a 1984 statement of intent for what we would now call **automated diagnostic AI + continuously-learning data infrastructure**. It directly anticipates (a) the 1994 group's own expert-system realization and (b) the broader continuously-learning EHR-AI feedback loop concept the FDA's PCCP / TPLC framework now governs (see [fda-510k-pathway](../concepts/fda-510k-pathway.md)).

3. **Specialty-specific origin of the imaging-AI ladder.** The same three-rung pattern that recurs across medical AI — quantitative imaging → statistical/expert-system classifier → neural network — has [stephen-klyce](../entities/stephen-klyce.md)'s group as the primary investigator for all three rungs in corneal topography. This 1984 paper is rung one.

## Notes

- **Historical positioning.** This is *not* a clinical AI paper in the modern sense; the word "AI" does not appear. But the architectural vision in the discussion explicitly maps the expert-system territory, and the data-analysis system this paper describes is the platform on which the group's later AI work (1994 expert system, 1995 neural network, 1997 systematic neural-network comparison) is built.
- **Hardware constraint context.** The 64 KB max compiled program size and minute-scale manual digitization-per-photograph are direct consequences of PDP 11/34A constraints and would be irrelevant by the time the 1994 [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) work uses an integrated TMS-1 videokeratoscope.
- **Citation precedence**: this is the **primary** source for the quantitative-corneal-topography pipeline; later reviews ([ogut-ai-clinical-medicine-2025](ogut-ai-clinical-medicine-2025.md), the Lozano-Castaneda *Diagnostics* MDPI 2023 keratoconus-AI review, etc.) cite it as foundational.
- **Acknowledgments**: programs written on the LSU/Lions Eye Research Computer Facility (UNIX courtesy of Bell Labs); H. E. Kaufman pointed out the need for the work; J. D. Doss and R. W. Baltosser shared programs and data; C. Kelley selected patient photographs; C. E. Crosson designed the plotter hardware interface and graphics program.

## Entities and concepts touched

- [stephen-klyce](../entities/stephen-klyce.md) — sole author; foundational entry in his AI-relevant publication record.
- [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) — rung one of the lineage this concept page traces.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — quantitative-imaging-AI ancestry for the ophthalmology section.
- [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md) and [agentic-clinical-ai](../concepts/agentic-clinical-ai.md) — the closed-loop `diagnose` + `learn` architecture sketched in this paper's discussion is a conceptual ancestor of continuous-learning agentic systems.
