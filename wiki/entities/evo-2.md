---
type: entity
title: Evo 2
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [model-family/foundation-model, biomedical-ai/genomics, organization/arc-institute, organization/nvidia, organization/stanford]
---

# Evo 2

A **40-billion-parameter genomic foundation model** trained on DNA sequences from across the tree of life. Released 2025 by **Arc Institute**, in collaboration with **Nvidia, Stanford University, and UC Berkeley**.

## Specs

| Property | Value |
|---|---|
| Parameters | **40B** |
| Context length | **1 million tokens** |
| Training corpus | **OpenGenome2** — 9.3 trillion DNA base pairs from all domains of life |
| License | **Fully open release** |
| Release year | 2025 |
| Capability | Genome-scale generation; predict cellular responses to drugs and genetic perturbations |

## Why it matters

Evo 2 is the **flagship example** of the 2025 wave of "virtual cell" / genomic foundation models — systems that aim to predict cellular responses to drugs and genetic perturbations *without running wet-lab experiments*. The category includes:

- **Evo 2** (Arc Institute) — DNA language model.
- **STATE** — perturbation-response model.
- **AlphaGenome** (DeepMind) — multimodal, single-base-pair-resolution genomic FM.
- **GPN-Star** (200M params) — focused on functional and regulatory genomics.

## The "scale isn't enough" finding

A surprising 2025 result: **GPN-Star (200M parameters) outperformed Evo 2 (40B) on multiple variant effect prediction tasks**.

| Model | Parameters | AUPRC on virtual cell perf benchmark (Ye et al., 2025) |
|---|---|---|
| Enformer | 250M | 0.38 |
| Borzoi | 190M | 0.40 |
| Evo 2 | **40B** | 0.53 |
| **GPN-Star** | **200M** | **0.75** |

The takeaway from the AI Index: **scale alone is not yet sufficient** in genomic foundation models, and **training method and data curation remain important determinants** of performance. This mirrors the [protein-language-models](../concepts/protein-language-models.md) finding — MSAPairformer (111M) > ESM3 (98B) on ProteinGym.

## Where Evo 2 fits in the diagnostic pipeline

Evo 2 isn't a diagnostic tool itself, but it underpins:
- **Variant effect prediction** — informing genomic diagnostics for inherited disease.
- **Drug-target identification** — input to companion-diagnostic development.
- **Synthetic biology / therapeutic design** — links upstream of personalized medicine.

The AI Index notes (Ch. 5.2, p. 244–245) that Evo 2's 1M-token context window enables genome-scale analysis tasks previously impossible at smaller context lengths — a structural capability advance, not just parameter growth.

## Open release

Evo 2 was released with **fully open weights**, contrasting with the closure trend in general-purpose AI (median Foundation Model Transparency Index score dropped from 58 to 40 in 2025). The AI Index notes that **most AI foundation models for science come from cross-sector collaborations**, in contrast to the industry-dominated landscape of general-purpose AI — Evo 2 is a paradigmatic example (Arc Institute non-profit + Nvidia industry + Stanford/Berkeley academic).

## Open questions

- How does Evo 2's apparent underperformance vs. GPN-Star generalize across genomic tasks? Is GPN-Star better only at specific variant effect prediction tasks, or broadly?
- What's the practical compute cost of using Evo 2 vs. specialized smaller models in a diagnostic lab setting?
- Will Evo 2 successors continue scaling, or pivot to specialization?
- What's the regulatory framing for genomic-FM-derived clinical decisions?

## Related
- [protein-language-models](../concepts/protein-language-models.md) — sibling model class.
- [cofolding-models](../concepts/cofolding-models.md) — structure-prediction sibling.
- [ai-index-2026](../sources/ai-index-2026.md) — primary source.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.1 Virtual Cell Models, p. 265–266; Ch. 5.2 Biological & Life Sciences foundation models table, p. 245)
