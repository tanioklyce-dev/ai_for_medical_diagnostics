---
type: concept
title: Protein language models (PLMs)
added: 2026-05-10
updated: 2026-05-10
sources: [[[ai-index-2026]]]
tags: [model-family/foundation-model, biomedical-ai/protein, evaluation/benchmark]
---

# Protein language models (PLMs)

Foundation models trained on protein sequence data, used for fitness prediction, function annotation, structure prediction (in concert with [[cofolding-models]]), and protein design. The 2025 inflection point: **a shift from scaling to specialization**, with smaller curated models beating larger generalist ones.

## The 2025 shift

In 2024, effort culminated in **ESM3 (98 billion parameters)**. In 2025, the focus turned to:
- Smaller architectures trained on **curated** data.
- Models augmented with **retrieval methods** (RAG-style).
- Fine-tuning for specialized tasks rather than general scaling.

## Performance on ProteinGym (Spearman correlation, 2021–25)

ProteinGym is the dominant benchmark — 250+ standardized deep-mutational-scanning assays with millions of mutated sequences and curated clinical datasets.

| Model | Year | Parameters | Avg. Spearman correlation |
|---|---|---|---|
| MSA-Transformer | 2021 | 100M | 0.45 |
| ESM-2 (150M / 3B / 650M) | 2022 | 150M–3B | 0.39–0.41 |
| **PoET** | 2023 | 200M | **0.47** |
| ESM-C (600M / 300M) | 2024 | 300M–600M | 0.40–0.41 |
| E1 (Single Sequence, 150M / 300M / 600M) | 2025 | 150M–600M | 0.40–0.42 |
| **MSA-Pairformer** | 2025 | **111M** | **0.45** |
| **E1 (Retrieval Augmented, 150M / 300M / 600M)** | 2025 | 150M–600M | **0.47–0.48** |

**MSA-Pairformer** (111M parameters) surpassed previous SOTA at a fraction of the training and parameter budget by leveraging multiple sequence alignments and physical constraints. The **Profluent E1** series similarly set new performance standards by combining a smaller model with retrieval-augmented generation.

## Notable models in the 2025 landscape

- **ESM3** (98B) — the giant; the *previous* paradigm.
- **MSA-Pairformer** (111M) — flagship example of small-model SOTA.
- **Profluent E1** series (single-sequence + retrieval-augmented variants).
- **ESM-C series** (300M–600M) — task-specific successors to ESM3, demonstrating that smaller models geared toward specific tasks (e.g., representation learning) can match the full ESM3 family on those tasks.
- **ProGen3** (46B) — large-scale generation model.
- **OpenCRISPR-1** — designed via fine-tuned 6B-parameter ProGen model; demonstrated improved specificity relative to standard SpCas9.

## Tasks that scale less with model size

Beyond ProteinGym, evidence is accumulating that:
- **Cellular localization prediction** varies more with training method and data than with parameter count.
- **CRISPR protein design** can be accomplished by fine-tuning a moderate-size model (6B ProGen → OpenCRISPR-1).
- Single-task representation learning doesn't need ESM3-scale capacity (ESM-C series).

## Where PLMs sit in the broader pipeline

Sequence → Structure → Function → Design

- **PLMs** handle the sequence side and link to function prediction.
- **[[cofolding-models]]** (AlphaFold 3 lineage) handle structure with mixed inputs.
- **Generative protein design**: BindCraft, Germinal (workflow-based), RFDiffusion, BoltzGen (directly trained for binders).

## Adaptyv Bio Nipah Binder Challenge (2025)

A controlled comparison of protein design methods on the task of designing a binder targeting Nipah virus. Of **1,000+ designs tested**:
- 99 confirmed to bind.
- **None** neutralized the targeted protein.
- Best method: **Mosaic** (combining multiple tools with expert tuning) — outperformed general-purpose approaches at 88.89% bound rate.
- BoltzGen: 98.13% expressed but only 1.87% bound.

The takeaway: pure generative methods produce expressible designs, but functional binding still requires expert-tuned multi-tool pipelines.

## Open questions

- How do PLMs compose with [[cofolding-models]] in end-to-end design pipelines?
- What's the data-quality vs. data-scale tradeoff for the next generation?
- Where does the field land on permissively-licensed open weights vs. commercial closure?

## Related
- [[cofolding-models]] — structure-prediction sibling.
- [[evo-2]] — DNA/genomic-scale analog.
- [[ai-index-2026]] — primary source.

## Sources
- [[ai-index-2026]] (Ch. 6.1, p. 261–262, 265)
