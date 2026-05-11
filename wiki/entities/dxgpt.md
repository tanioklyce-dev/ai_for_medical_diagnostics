---
type: entity
title: DxGPT (Foundation 29)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/do-olmo-dxgpt-rare-disease-2024.md]
tags: [task/diagnosis, model-family/llm, deployment, rare-disease, modality/primary-care]
---

# DxGPT

Free, web-based clinical decision-support tool for **rare-disease diagnosis**, built by [foundation29](foundation29.md) (2017–) and launched in **2023**. Runs on Microsoft Azure OpenAI Service; production backend is **GPT-4o** with **o1** integrated as of 2025. Positioned explicitly as decision support, **not a medical device**.

## What it does

Clinician (or patient) enters a free-text symptom description; DxGPT returns a ranked list of candidate rare diseases plus explanations. Intended workflow: clinician uses the differential as a starting point, refines via further clinical data and lab tests, makes final diagnosis. The tool **does not store personally identifying information** and does not request names, addresses, or surnames; GDPR-compliant; reported to have passed ethics-committee review at deploying hospitals.

## Deployment scale (as of 2025, per Microsoft feature article)

- **>500,000 users globally** (US, Europe, India, China).
- **Madrid public healthcare system** integration since late 2023; **~6,000 doctors** have access.
- Two major Madrid hospitals scheduled for expanded implementation in 2025.
- Planned future expansion to other European healthcare systems and Azure Marketplace.

This makes DxGPT one of the few **large-N deployed LLM-based clinical copilots** in mid-2020s clinical AI, alongside [ai-consult-penda](ai-consult-penda.md) and ambient-scribe systems like [abridge](abridge.md).

## Evaluation evidence

The primary methodological evaluation is the team's own preprint, [do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md). DxGPT runs on GPT-4-family models in production; that paper benchmarks **13 frontier LLMs** (GPT-4 family, Claude 3 Opus/Sonnet, Gemini 1.5 Pro, Llama 2/3 family, Mistral, Mixtral, Cohere Command R+) on the same rare-disease diagnostic task across one synthetic and two real-world datasets.

### Key numbers

| Dataset | Best closed model | P1 | P1+P5 |
|---|---|---|---|
| Synthetic (200 GPT-4 Orphanet cases) | Claude 3 Opus | 72.5% | 91.5% |
| Synthetic | GPT-4 Turbo 1106 | 68.5% | **92.0%** |
| **RAMEDIS** (HPO lists, n=200) | Claude 3 Opus | **55.0%** | **70.0%** |
| **PUMCH** (HPO lists, n=75) | GPT-4 Turbo 1106 | **59.5%** | **64.9%** |

Open-model standouts: **Llama 3 70B** rivals closed models on synthetic data (64% / 90.5%) and is the best open model on all real-world datasets. **Mixtral 8x22B** reaches 67.5% / 87.0% on synthetic. Smaller open models (Llama 2 7B, Mistral 7B) trail meaningfully on real-world cases.

### Synthetic-to-real-world gap

A consistent **10–30-percentage-point drop in P1 accuracy** between synthetic and real-world (RAMEDIS/PUMCH) datasets across all 13 models. The cleanest in-paper demonstration of the [clinical-validation](../concepts/clinical-validation.md) gap: GPT-4-generated synthetic cases overstate deployment-grade performance on the rare-disease task. PUMCH (Peking Union Medical College Hospital, China-origin) is the hardest of the three datasets.

### Methodological caveats

- **GPT-4 generates the synthetic cases AND acts as judge** scoring all 13 models' outputs — circularity acknowledged (§4.4.2, Shankar 2024 caveat).
- **No human-physician comparison** in the preprint — RareBench cases have ground-truth labels but were not co-evaluated by clinicians blindly.
- **Preprint, not peer-reviewed.**

## Regulatory framing

DxGPT is explicitly **not a medical device**. Foundation 29's framing: decision support to aid clinical reasoning; final diagnosis remains the clinician's responsibility. Same framing used by other deployed LLM copilots like [ai-consult-penda](ai-consult-penda.md) and ambient scribes; it sidesteps strict FDA SaMD authorization but creates its own evidence-base questions (see [clinical-validation](../concepts/clinical-validation.md)).

## Open questions

- **Deployment outcomes evidence.** The 500k-user and Madrid-system figures are operational counts; no published evidence yet on time-to-diagnosis reduction, accuracy improvement vs unaided clinicians, or patient outcomes. The Foundation 29 team has stated (§5.1 of the preprint) that real-world clinical studies are underway.
- **Model version drift.** Production runs on GPT-4o / o1; the 2024 preprint evaluates GPT-4 0613 / Turbo 1106 / Turbo 0409. The benchmarked-version vs production-version mismatch should be tracked when next-gen evaluation lands.
- **Coverage.** Synthetic cases derive from top 200 Orphanet rare diseases; real-world datasets are RAMEDIS (mixed origin) and PUMCH (Chinese cases). Coverage of geographically underserved rare-disease cohorts is unaddressed.
- **Calibration.** Top-5 accuracy is operationally meaningful only if the model communicates appropriate uncertainty about which of the 5 candidates is most likely.

## Related
- [foundation29](foundation29.md) — the nonprofit that builds and runs DxGPT.
- [rare-disease-diagnosis](../concepts/rare-disease-diagnosis.md) — the task context.
- [ai-consult-penda](ai-consult-penda.md) — the other large-N deployed LLM copilot.
- [mai-dxo](mai-dxo.md) — Microsoft research's orchestrator on NEJM CPCs; distinct architecture, no real-care deployment.
- [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md) — broader benchmark context.
- [clinical-validation](../concepts/clinical-validation.md) — synthetic-vs-real-world gap context.

## Sources
- [do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md) — primary citation for evaluation methodology.
- Microsoft Source EMEA feature, *"A father's quest for diagnosis inspired a disruptive AI solution"*: <https://news.microsoft.com/source/emea/features/a-fathers-quest-for-diagnosis-inspired-a-disruptive-ai-solution/>
- DxGPT website: <https://dxgpt.app/>
