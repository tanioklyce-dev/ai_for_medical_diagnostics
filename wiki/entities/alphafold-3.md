---
type: entity
title: AlphaFold 3
added: 2026-05-10
updated: 2026-05-10
sources: [[[ai-index-2026]]]
tags: [model-family/foundation-model, biomedical-ai/structure-prediction, organization/google-deepmind]
---

# AlphaFold 3

The flagship cofolding model — **predicts 3D structures formed by combinations of proteins, nucleic acids, drugs, and other biomolecules** simultaneously. Released by **Google DeepMind** in 2024.

## Specs

| Property | Value |
|---|---|
| Parameters | **370M** |
| Year | 2024 |
| Developer | Google DeepMind |
| Capability | Cofolding (proteins + nucleic acids + small molecules + ligands) |
| License | Restricted (academic/non-commercial) — see open-source replications below |

## Why it matters

AlphaFold 3 inaugurated the **cofolding paradigm** — moving beyond AlphaFold 2's protein-only structure prediction to handle the more clinically and pharmaceutically relevant problem of **protein-ligand and protein-nucleic-acid complexes**. This is foundational for drug discovery and informs downstream diagnostic-companion biomarker work.

## FoldBench (2024–25): still leading

FoldBench is a benchmark that tests whether a model can correctly predict how a small molecule (e.g., drug candidate) physically binds to a target protein. AlphaFold 3 holds the leading position despite multiple larger models being released since:

| Model | Parameters | FoldBench accuracy |
|---|---|---|
| Chai-1 | 440M | 51.23% |
| HelixFold3 | 370M | 51.82% |
| Boltz-1 | 610M | 55.04% |
| **AlphaFold 3** | **370M** | **64.90%** |
| Protenix v0.7 | 368M | 50.70% |
| Boltz-2 | 521M | 53.90% |
| RosettaFold-3 | 730M | 57.28% |
| SeedFold | 923M | 63.10% |

**Bigger models have not surpassed AlphaFold 3's 64.9%** — see [[cofolding-models]] for the data-not-scale-bottleneck framing.

## Training data (per AI Index Figure 6.1.6¹)

| Source | Used? |
|---|---|
| Experimental structural data | ✓ |
| Distilled structural data (AI-predicted) | ✓ |
| Molecular dynamics | — |
| Binding affinity measurements | ✓ |
| RNA structure | — |

Distilled datasets — AI-predicted protein structures supplementing experimentally-determined ones — expand training sets from hundreds of thousands of entries to tens of millions.

## Open-source replications (2025)

Multiple cofolding models in 2025 were inspired by AlphaFold 3's architecture, several released under **commercially permissive licenses** — important for medical AI deployment:

- **Boltz-2** (commercially permissive)
- **OpenFold3** (commercially permissive; adds RNA structure as a training signal)
- **SimpleFold**
- **Chai-1**
- **HelixFold3**

## Where AlphaFold 3 fits in diagnostics

Like [[evo-2]], AlphaFold 3 is upstream of clinical diagnostics rather than a diagnostic tool itself. Its diagnostic-relevant impact comes through:
- **Drug discovery** → companion biomarkers → diagnostic test development.
- **Target validation** in rare disease.
- **In silico binding prediction** for therapeutic stratification.

## Open questions

- Will the FoldBench gap close as cofolding models incorporate RNA structure, MD simulations, and richer binding affinity datasets?
- What's the practical accuracy threshold above which cofolding predictions can substitute for crystallography or cryo-EM in early drug discovery?
- How does AlphaFold 3's restricted license interact with academic medical-center research and downstream commercial diagnostic development?

## Related
- [[cofolding-models]] — the broader model family.
- [[protein-language-models]] — sequence-side complement.
- [[ai-index-2026]] — primary source.

## Sources
- [[ai-index-2026]] (Ch. 6.1 Structure Prediction and Cofolding Models, p. 262–264)
