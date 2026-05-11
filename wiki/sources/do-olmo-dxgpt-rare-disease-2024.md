---
type: source
title: Assessing DxGPT — Diagnosing Rare Diseases with Various Large Language Models (do Olmo et al., 2024)
authors: [Juanjo do Olmo, Javier Logroño, Carlos Mascías, Marcelo Martínez, Julián Isla]
published: 2024-05-09
ingested: 2026-05-10
source_path: raw/do-olmo-dxgpt-rare-disease-2024.pdf
url: https://www.medrxiv.org/content/10.1101/2024.05.08.24307062v1
doi: 10.1101/2024.05.08.24307062
journal: medRxiv preprint (not peer-reviewed)
pages: 13
code: https://github.com/foundation29org/dxgpt_testing/
tags: [task/diagnosis, modality/primary-care, evaluation/external-validation, model-family/llm, concern/generalization, rare-disease]
---

# Assessing DxGPT — Diagnosing Rare Diseases with Various Large Language Models

> Foundation 29 team preprint (do Olmo, Logroño, Mascías, Martínez, Isla; medRxiv 10.1101/2024.05.08.24307062v1, May 9 2024). Benchmarks **13 frontier LLMs** — six closed (GPT-4 0613/Turbo 1106/Turbo 0409, Claude 3 Opus/Sonnet, Gemini 1.5 Pro) and seven open (Llama 2 7B, Llama 3 8B/70B, Mistral 7B, Mixtral 8x7B/8x22B, Cohere Command R+) — on rare-disease diagnostic accuracy across one synthetic and two real-world datasets. **Strict Accuracy (P1)** and **Top-5 Accuracy (P1+P5)** are the headline metrics. Companion paper to the deployed [dxgpt](../entities/dxgpt.md) consumer/clinician tool from nonprofit [foundation29](../entities/foundation29.md). Preprint, **not peer-reviewed**.

## Summary

Rare-disease diagnosis is the canonical "diagnostic odyssey" problem: 5,000–10,000 named conditions; **56.4% of patients experience >1 year diagnostic delay** (Benito-Lozano 2022, Spanish registry); **>45% remain undiagnosed or misdiagnosed** (Molster 2016, Australian survey). The Foundation 29 team — founded by Microsoft engineer Julián Isla after his son was diagnosed with Dravet syndrome — built DxGPT as a free, web-based decision-support tool to assist clinicians in this space. The platform runs on Azure OpenAI Service and uses GPT-4 in production; this preprint evaluates 13 alternative LLMs on the same task.

The methodology rests on three datasets and two evaluation metrics. **Synthetic cases (n=200)** are GPT-4-generated symptom paragraphs derived from the top 200 Orphanet rare diseases — designed to be subtle ("Do not explicitly state {disease}"). **RAMEDIS (n=200)** and **PUMCH (n=75)** are real-world rare-disease cases from RareBench (Chen 2024 ArXiv 2402.06341), each represented as Human Phenotype Ontology (HPO) symptom lists. Metrics: **P1** (top-1 correct) and **P1+P5** (correct in top 5 suggestions). Models are queried via a single standardized "differential-with-explanations" prompt; outputs are compared against ground truth by **GPT-4 acting as an automated judge** with explicit P1/P5/P0 instructions.

Results show a sharp and consistent **synthetic-vs-real-world gap**. On synthetic cases, closed models cluster at 65–73% P1 and 88–92% P5 (Claude 3 Opus 72.5% / GPT-4 Turbo 1106 92% lead); Llama 3 70B (open) reaches 64% / 90.5%, rivaling closed models. On **RAMEDIS**, closed-model P1 falls to 42–55% (Claude 3 Opus 55%/70% leads; Gemini 1.5 Pro is the worst closed model at 42.6%/51%). On **PUMCH**, the floor drops further: best is **GPT-4 Turbo 1106 at 59.46% P1 / 64.86% P5**. Across all three datasets, GPT-4 variants are consistently top-tier but show internal variance — GPT-4 Turbo 1106 outperforms GPT-4 Turbo 0409 on PUMCH, while the reverse holds on RAMEDIS. Open models span a wide range: Llama 3 70B and Mixtral 8x22B punch near closed models on synthetic data, while Llama 2 7B and Mistral 7B fall below 32% P1 on real-world cases.

What's notable for this wiki:
- This is the **primary methodological citation** for [dxgpt](../entities/dxgpt.md), a deployed clinical-AI tool in the Madrid public health system (~6,000 doctors, two hospitals expanding 2025) — making it one of the few large-N deployed LLM copilots alongside [ai-consult-penda](../entities/ai-consult-penda.md). Where [mai-dxo](../entities/mai-dxo.md) orchestrates frontier LLMs against NEJM CPCs for academic benchmarking, DxGPT puts a single LLM behind a free web UI for real clinicians worldwide.
- The **synthetic-to-real-world accuracy drop** (≈10–30 P1 percentage points, model-dependent) is the clearest in-paper demonstration of the [clinical-validation](../concepts/clinical-validation.md) gap on a rare-disease task: GPT-4-generated cases overstate deployment performance vs real HPO-encoded patient phenotypes.
- The paper uses **GPT-4 to generate synthetic cases AND as the LLM judge that scores all 13 models**. The authors acknowledge this circularity in §4.4.2 ("the use of LLMs as automatic evaluators for batch examining the results against ground truths presents its own set of challenges as stated in Shankar et al. [17]. This method, while efficient, might overestimate the models' performance"). A material methodological caveat that limits the strength of any single P1/P5 number.

## Key claims and findings

### Methodology (§2)
- **Datasets**: 200 GPT-4-generated synthetic Orphanet cases; 200 RAMEDIS HPO-list cases; 75 PUMCH HPO-list cases. RAMEDIS and PUMCH from RareBench (Chen 2024 ArXiv 2402.06341).
- **Metrics**: Strict Accuracy = P1 (top-1 match); Top-5 Accuracy = P1+P5 (correct anywhere in top 5).
- **Models**: 13 total; 6 closed (GPT-4 0613, GPT-4 Turbo 1106, GPT-4 Turbo 0409, Claude 3 Opus, Claude 3 Sonnet, Gemini 1.5 Pro), 7 open (Llama 2 7B, Llama 3 8B/70B, Mistral 7B, Mixtral 8x7B/8x22B, Cohere Command R+).
- **Pipeline**: Standardized diagnostic prompt → per-model differentials → GPT-4 LLM-judge classifies outputs as P1/P5/P0. Code: <https://github.com/foundation29org/dxgpt_testing/>.
- **Prompts**: Synthetic-case-generation, diagnostic, and evaluation prompts reproduced verbatim in Appendix §6.

### Results (§3, Tables 1–6)

**Synthetic dataset (n=200), closed models**

| Model | P1 | P1+P5 |
|---|---|---|
| GPT-4 0613 | 66.5% | 90.5% |
| GPT-4 Turbo 1106 | 68.5% | **92.0%** |
| GPT-4 Turbo 0409 | 67.0% | 91.0% |
| **Claude 3 Opus** | **72.5%** | 91.5% |
| Claude 3 Sonnet | 65.5% | 88.5% |
| Gemini 1.5 Pro | 70.0% | 91.0% |

**Synthetic dataset, open models**

| Model | P1 | P1+P5 |
|---|---|---|
| Llama 2 7B | 30.5% | 58.0% |
| Llama 3 8B | 48.2% | 74.1% |
| **Llama 3 70B** | 64.0% | **90.5%** |
| Mistral 7B | 47.0% | 70.5% |
| Mixtral 8x7B | 56.5% | 84.5% |
| **Mixtral 8x22B** | **67.5%** | 87.0% |
| Cohere Command R+ | 54.0% | 80.0% |

**RAMEDIS (n=200), closed models**

| Model | P1 | P1+P5 |
|---|---|---|
| GPT-4 0613 | 50.25% | 63.32% |
| GPT-4 Turbo 1106 | 51.50% | 67.50% |
| GPT-4 Turbo 0409 | 54.04% | 68.69% |
| **Claude 3 Opus** | **55.00%** | **70.00%** |
| Claude 3 Sonnet | 50.50% | 64.50% |
| Gemini 1.5 Pro | 42.63% | 51.05% |

**PUMCH (n=75), closed models**

| Model | P1 | P1+P5 |
|---|---|---|
| GPT-4 0613 | 44.00% | 53.33% |
| **GPT-4 Turbo 1106** | **59.46%** | **64.86%** |
| GPT-4 Turbo 0409 | 47.30% | 58.11% |
| Claude 3 Opus | 52.05% | 61.64% |
| Claude 3 Sonnet | 33.33% | 48.00% |
| Gemini 1.5 Pro | 47.30% | 54.05% |

Open-model real-world numbers: Llama 3 70B is the consistent best open model (53.54% / 62.12% on RAMEDIS; 44.44% / 48.61% on PUMCH). Mixtral 8x22B, Cohere Command R+, and the smaller Llama / Mistral variants trail.

### Discussion (§4)
- "Closed models like GPT-4, Claude, and Gemini exhibited relatively high accuracy on the synthetic rare disease dataset, with Strict Accuracy ranging from 65.5% to 72.5% and Top-5 Accuracy from 88.5% to 92%." (§4.1)
- "Accuracy dropped notably on real-world datasets like RAMEDIS and PUMCH compared to synthetic cases, as expected." (§4.2)
- "Llama 3 70B stood out as a strong performer, achieving the highest accuracy among open models on all three datasets. It even rivaled some of the closed models, especially on the synthetic data (64% Strict Accuracy, 90.5% Top-5 Accuracy)." (§4.3)
- Variability framing (§4.3): even within GPT-4 variants, dataset-specific reversals (Turbo 1106 vs Turbo 0409 swap between RAMEDIS and PUMCH) argue against single-model evaluation.

### Stated limitations (§4.4.2)
1. **No direct clinical validation** — "the practical utility of the AI models in real-world clinical settings remains untested."
2. **Synthetic-data bias** — "the synthetic dataset, generated using GPT-4, may carry biases inherent to the model."
3. **Real-world coverage** — RAMEDIS/PUMCH "may not fully represent the diversity of rare diseases."
4. **No human-expert comparison** — "no direct comparison with the diagnostic accuracy of human experts."
5. **LLM-as-judge circularity** (Shankar 2024 caveat) — "this method, while efficient, might overestimate the models' performance."
6. **No interpretability analysis.**

### Future work (§5)
- §5.1 declares **real-world clinical studies are already initiated** "with real doctors and human evaluators in different hospitals and healthcare systems."
- Multimodal integration (imaging + EHR); knowledge graphs (Chandak 2023 PrimeKG); many-shot in-context learning; hybrid LLM + reasoning-engine architectures.

## Entities and concepts touched

- [dxgpt](../entities/dxgpt.md) — the deployed product this paper benchmarks.
- [foundation29](../entities/foundation29.md) — the nonprofit that builds and operates DxGPT.
- [rare-disease-diagnosis](../concepts/rare-disease-diagnosis.md) — the clinical task this paper situates within.
- [clinical-validation](../concepts/clinical-validation.md) — the synthetic-vs-real-world accuracy gap; LLM-as-judge circularity is a new methodological caveat to track.
- [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md) — adds a 2024 13-model rare-disease benchmark to the single-LLM-baseline picture; introduces RAMEDIS / PUMCH / RareBench.
- [ai-hallucination-medical](../concepts/ai-hallucination-medical.md) — relevant via "differentials with explanations" output format; not directly evaluated.
- [ai-consult-penda](../entities/ai-consult-penda.md) — parallel large-N deployed-LLM-copilot exemplar.
- [mai-dxo](../entities/mai-dxo.md) — the academic-benchmark counterpart from Microsoft research on NEJM CPCs.

## Notes

### Pre-existing wiki context this paper sharpens
- [ai-consult-penda](../entities/ai-consult-penda.md) has been the wiki's anchor for "first prospective LLM copilot in real care." DxGPT is a parallel deployment with very different shape: free web tool, decision-support framing, 500k+ self-served users in addition to the Madrid public-system integration (~6,000 doctors); no comparable RCT-grade outcomes evidence yet. The two are **complementary deployment case studies** for the LLM-as-real-care-copilot category framed in [overview](../overview.md).
- The synthetic-to-real-world drop is consistent with [mai-dxo-sequential-diagnosis-2025](mai-dxo-sequential-diagnosis-2025.md)'s framing: off-the-shelf-LLM accuracy on curated benchmarks systematically overstates deployment-grade performance. The DxGPT paper provides a **rare-disease analog** to the NEJM CPC sequential-diagnosis story.
- The [arise-state-of-clinical-ai-2026](arise-state-of-clinical-ai-2026.md) framing of LLM clinical reasoning is dominated by case-bench evaluation (NOHARM, MedQA, HealthBench). DxGPT's RAMEDIS/PUMCH HPO-list evaluation is **a different shape of test** — short symptom lists (typical of rare-disease referral) rather than full case narratives.

### Methodological caveats worth keeping front-of-mind
- **GPT-4-as-generator + GPT-4-as-judge.** Synthetic cases come from GPT-4; all model outputs are judged by GPT-4. Both ends of the pipeline favor GPT-4-family results in ways the paper acknowledges. Open-model numbers in particular may be artificially deflated by the judge's stylistic preferences.
- **HPO-list inputs differ from real-clinic inputs.** RAMEDIS/PUMCH represent patients as canonical HPO symptom codes. A real clinician does not present that way; deployment performance on free-text narratives may differ in either direction.
- **No p-values in main text** despite being computed; authors note (§4.4.2) they "have chosen not to discuss these statistical details in the main text of the paper, as they do not align with the primary objectives." A peer-reviewed version would normally surface them.
- **Sample sizes are small** — particularly PUMCH at n=75. Per-model differences on PUMCH should not be over-interpreted.
- **Preprint, not peer-reviewed.** Per medRxiv banner: "should not be used to guide clinical practice."

### Follow-up questions surfaced
- Does the in-progress clinical study (§5.1) compare DxGPT to clinicians head-to-head in Madrid public-system deployment? If so, the resulting paper would be a major upgrade.
- How does Llama 3 70B (free / open) actually compare to GPT-4 on the *real-world* HPO-list task? Open-model gap is dataset-dependent.
- What's the calibration story for top-5? P5 of 90% is useful only if the model expresses appropriate uncertainty about which of the 5 is most likely.
- Coverage equity: do the Orphanet-derived synthetic cases skew toward Western/European patient cohorts? Geographic equity of diagnostic accuracy is unaddressed.

### Code and reproducibility
- Code: <https://github.com/foundation29org/dxgpt_testing/> — synthetic-dataset generation, model inference, automatic-evaluation pipeline. Cited in §2.4 and §6.
- Prompts (synthetic-case generation, diagnostic, evaluation) reproduced verbatim in Appendix §6 — directly reusable for replication or extension to additional LLMs.
