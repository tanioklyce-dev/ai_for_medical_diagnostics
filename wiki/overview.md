---
type: overview
title: AI for Medical Diagnostics — Overview
added: 2026-05-10
updated: 2026-05-10
sources: [sources/ai-index-2026.md]
tags: [overview]
---

# AI for Medical Diagnostics — Overview

*Top-level synthesis. Updated 2026-05-10 after first domain-source ingest. Will continue to evolve.*

## State of the field as of early 2026 (per [ai-index-2026](sources/ai-index-2026.md))

Clinical AI moved from pilot programs to enterprise-scale deployments in 2025. The deployment story is real — multi-site outcomes evidence is accumulating for **narrow tools operating in constrained workflows under clinician oversight**. But the broader evidence base remains thin: a Stanford-Harvard ARISE Network review of 500+ clinical AI studies found **only 5% used real clinical data**.

The field is bifurcating along this evidence axis:

- **Strong evidence track**: ambient scribes, sepsis prediction, narrow imaging triage tools — clinician-in-loop, well-defined input/output, multi-site outcomes papers.
- **Capability-ahead-of-evidence track**: open-ended LLM clinical reasoning, multi-agent diagnostic systems, foundation models for medical imaging — strong benchmark performance, thin real-world validation, hallucination/factuality concerns.

## Five organizing axes (entry points to the wiki)

### 1. The evidence-validation axis
- **[clinical-validation](concepts/clinical-validation.md)** — the central tension. ARISE 5%/half-study finding. Prospective trials growing 28.5% YoY but still small relative to publication volume.
- **[arise-network](entities/arise-network.md)** — meta-evaluator publishing the *State of Clinical AI Report*.
- **[fda-510k-pathway](concepts/fda-510k-pathway.md)** — the regulatory substrate; substantial-equivalence-not-RCT model; 1,357 cumulative cleared devices.

### 2. The diagnostic-modality axis
- **[medical-imaging-ai](concepts/medical-imaging-ai.md)** — 76.6% of cleared devices, but data ~100x smaller than general; cross-model benchmarking still weak.
- Specialty depth in [medical-imaging-ai](concepts/medical-imaging-ai.md): cardiology, oncology, ophthalmology, pathology, radiology each have their own model & FDA-cleared product lineup.

### 3. The reasoning / agentic axis
- **[llm-clinical-reasoning](concepts/llm-clinical-reasoning.md)** — single-LLM benchmark performance now exceeds physician case-bench scores (o1-preview NEJM Healer: 78/80 vs. attendings 28/80; management reasoning 86% vs. 34%).
- **[agentic-clinical-ai](concepts/agentic-clinical-ai.md)** — multi-agent systems gain 7–60% over single-agent baselines.
- **[mai-dxo](entities/mai-dxo.md)** — flagship: 85.5% on NEJM cases vs. ~20% for 21 experienced physicians.
- All gated by the case-bench-vs-real-practice translation problem.

### 4. The deployed-clinical-AI axis
- **[ambient-ai-scribes](concepts/ambient-ai-scribes.md)** — biggest 2025 deployment story; **[abridge](entities/abridge.md)** at 150+ health systems.
- **[trews](entities/trews.md)** — sepsis early warning, 18.7% mortality reduction, 13 Cleveland Clinic hospitals.
- These are the case studies for the *strong evidence track*.

### 5. The biomedical-foundation-model axis
- **[protein-language-models](concepts/protein-language-models.md)** — 2025 shift from scaling (ESM3, 98B) to specialization (MSAPairformer, 111M, beats SOTA).
- **[cofolding-models](concepts/cofolding-models.md)** — [alphafold-3](entities/alphafold-3.md) still leads FoldBench at 64.9%; data, not scale, is the bottleneck.
- **[evo-2](entities/evo-2.md)** — 40B-parameter genomic FM; outperformed by 200M GPN-Star on variant effect prediction. "Scale alone isn't sufficient."
- These are upstream of clinical diagnostics but feed into diagnostic-test development and personalized medicine.

## Cross-cutting risk: hallucination and the diagnostic-LLM failure mode

- **[ai-hallucination-medical](concepts/ai-hallucination-medical.md)** — KaBLE benchmark shows GPT-4o accuracy collapses from 98.2% on third-person facts to 64.4% on first-person false beliefs. The AI Index frames this directly as a medical-diagnostic risk: "a model used to support a medical diagnosis based on a patient's mistaken belief, as opposed to an established fact, could reinforce an inaccurate diagnosis and treatment plan."
- AA-Omniscience hallucination rates: 22%–94% across 26 leading models, with explicit health-domain breakouts.
- NOHARM benchmark: 11.8–14.6 severely harmful recommendations per 100 cases for general-purpose LLMs in open-ended clinical reasoning.

## Frontier topics with thinner first-source coverage

- **[digital-twins-medicine](concepts/digital-twins-medicine.md)** — large publication/patent growth; only 12.1% of studies meet NASEM definition; Twin Health diabetes RCT (n=150) is the strongest result.
- Multimodal biomedical AI publications grew 2 (2021) → 462 (2025). Vision-language and vision-omics models are the leading subcategories.
- Patient perspectives literature grew 9 (2020) → 102 (2025); demographic disparities in acceptance documented; provider endorsement is the key determinant.

## Working hypothesis to revise as more sources arrive

> The 2026 state of the field is **two-track**. Diagnostic AI succeeding in production looks unsexy — narrow tools, clinician-in-loop, well-defined workflows. The headline-grabbing AI (autonomous diagnosis, multi-agent reasoning, foundation models for medicine) generates impressive benchmark numbers but lacks the prospective patient-outcome evidence that should govern clinical adoption. Bridging the gap is the next 2–3 years' work, and depends as much on benchmarking infrastructure, regulatory iteration (PCCPs under the [fda-510k-pathway](concepts/fda-510k-pathway.md)), and meta-evaluation ([arise-network](entities/arise-network.md)) as on model capability.

## Sources awaiting ingest in `raw/`
- `raw/claudes-constitution_webPDF_26-02.02a.pdf` — Anthropic, Claude's Constitution. Methodology/model-behavior document; relevance to medical diagnostics is indirect (deployment-safety, refusal behavior in clinical contexts) — TBD on ingest.

## Open questions to drive sourcing
- The full **ARISE *State of Clinical AI Report*** (Jan 2026) — most-cited evidence-base critique; ingest as primary source.
- The **Microsoft MAI-DxO primary publication** — verify the 85.5% vs. ~20% physician comparison methodology.
- The **TREWS / COMPOSER primary publications** — verify the prospective deployment effect sizes.
- Recent **NEJM AI** and **JAMA Network Open** issues for the prospective imaging trials (MASAI, NOTIFY-1, NOTIFY-EXTEND).
- **FDA 510(k) AI/ML device database** for current cleared-device list and labeling claims.
- Stanford Health Care's **FURM framework** documentation (governance counterpart).
- **State of clinical AI in non-US contexts** — the 2026 AI Index notes most patient-perception studies originate in U.S./U.K./Germany; equity-focused literature is overwhelmingly skewed to high-income contexts.
