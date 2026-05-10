---
type: concept
title: Cofolding models
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [model-family/foundation-model, biomedical-ai/structure-prediction, evaluation/benchmark]
---

# Cofolding models

A class of structure-prediction models that **predict 3D structures formed by combinations of proteins, nucleic acids, drugs, and other biomolecules** simultaneously — rather than just protein-only structures. Inaugurated by [alphafold-3](../entities/alphafold-3.md) (2024), with a community of open-source replications and extensions in 2025.

## Why cofolding matters

Traditional structure prediction (AlphaFold 2, RoseTTAFold) handled proteins in isolation. Cofolding tackles the more clinically relevant problem: **how a small molecule (drug candidate) physically binds to a target protein**, or how protein-RNA-ligand complexes assemble. This is foundational for drug discovery and a key reason for the surge in [ai-index-2026](../sources/ai-index-2026.md)-tracked AI-for-drug-discovery publications (431 in 2018 → 3,311 in 2025).

## The 2025 cofolding model lineup

| Model | Year | Params | Training data | License |
|---|---|---|---|---|
| **AlphaFold 3** | 2024 | 370M | Experimental + distilled structural | Restricted |
| HelixFold3 | 2024 | 370M | Experimental | — |
| Chai-1 | 2024 | 440M | Experimental | — |
| Boltz-1 | 2024 | 610M | Experimental + distilled | — |
| **Boltz-2** | 2025 | 521M | Experimental + distilled + molecular dynamics + binding affinity | Commercially permissive |
| Protenix-Tiny | 2025 | 109M | — | — |
| Protenix-Mini | 2025 | 135M | — | — |
| Protenix v0.7 | 2025 | 370M | — | — |
| SimpleFold | 2025 | 3B | Experimental + distilled + MD | — |
| RosettaFold-3 | 2025 | 730M | Experimental + distilled + binding affinity | — |
| **OpenFold3** | 2025 | 370M | Experimental + distilled + binding affinity + **RNA structure** | Commercially permissive |
| SeedFold | 2025 | 923M | — | — |

## FoldBench (cofolding accuracy benchmark, 2024–25)

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

**AlphaFold 3 (370M params, 64.9%)** still leads despite multiple larger models being released since.

## The data-not-scale bottleneck

Two findings together suggest **data, not parameter count, is the binding constraint**:

1. **Bigger ≠ better**: post-AlphaFold 3 models have converged on similar parameter scale (~400M–900M) rather than continuing to grow.
2. **Distilled datasets matter**: cofolding models can now represent all structure types in the Protein Data Bank (PDB). Further gains come from "distilled" datasets — AI-predicted protein structures supplementing experimentally determined ones, expanding training sets from hundreds of thousands of entries to **tens of millions**.

**Boltz-2** illustrates the complementary approach: training on both PDB structural data *and* experimental binding affinity measurements — combining specialization and scale.

## Training data sources by model (2025)

| Model | Experimental | Distilled | Molecular Dynamics | Binding Affinity | RNA Structure |
|---|---|---|---|---|---|
| AlphaFold 3 | ✓ | ✓ | | ✓ | |
| Boltz-2 | ✓ | ✓ | ✓ | ✓ | |
| SimpleFold | ✓ | ✓ | ✓ | | |
| OpenFold3 | ✓ | ✓ | | ✓ | ✓ |

Open-source replications of AlphaFold 3 — including **Boltz-2** and **OpenFold3** — were released under commercially permissive licenses, important for medical AI deployment.

## Why this matters for medical diagnostics

- Most diagnostics today are imaging or biomarker driven, not structure driven. But cofolding underpins **drug discovery and personalized therapeutics**, which connect downstream to diagnostic-companion biomarker panels.
- **In silico binding prediction** is increasingly relevant for rare disease and target validation — both inputs to diagnostic test development.
- Open licensing of Boltz-2 and OpenFold3 lowers the barrier for academic medical centers to do their own modeling.

## Related
- [alphafold-3](../entities/alphafold-3.md) — flagship entity.
- [protein-language-models](protein-language-models.md) — sequence-side complement.
- [evo-2](../entities/evo-2.md) — genomic-scale analog.
- [ai-index-2026](../sources/ai-index-2026.md) — primary source.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.1, p. 262–264)
