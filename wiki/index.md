---
type: index
updated: 2026-05-10
---

# Index

Content catalog for the AI-for-medical-diagnostics wiki. Updated on every ingest.

## Top-level
- [overview](overview.md) — evolving synthesis; **two-track + emerging-third** field framing (narrow-tool strong-evidence, open-LLM capability-ahead-of-evidence, LLM-as-real-care-copilot emerging)

## Sources
- [arise-state-of-clinical-ai-2026](sources/arise-state-of-clinical-ai-2026.md) — ARISE Network, *State of Clinical AI Report 2026* (Jan 2026, 130-slide deck). Primary citation chain for most clinical-AI claims; spine of the wiki.
- [mai-dxo-sequential-diagnosis-2025](sources/mai-dxo-sequential-diagnosis-2025.md) — Microsoft AI, *Sequential Diagnosis with Language Models* (Nori, Horvitz et al., ArXiv 2506.22405, Jul 2025). Primary for MAI-DxO orchestrator and SDBench methodology.
- [ai-index-2026](sources/ai-index-2026.md) — Stanford HAI, AI Index Report 2026 (April 2026, 425 pp). First edition with standalone Medicine and Science chapters.
- [ogut-ai-clinical-medicine-2025](sources/ogut-ai-clinical-medicine-2025.md) — Ogut single-author PRISMA-style review (MDPI *Clin. Pract.* Sept 2025, 150 studies across 5 domains). Useful as citation map to 2016–2021 landmarks (Gulshan, Rajkomar, Rodriguez-Ruiz, Attia, Försch, Vasey); methodologically light.
- [llm-wiki](sources/llm-wiki.md) — meta-document describing the LLM-wiki pattern this project uses *(methodology, not domain content)*

## Concepts
- [clinical-validation](concepts/clinical-validation.md) — central evidence-base tension; primary source for "5%" stat (Bedi/Shah JAMA Jan 2025, n=519 studies); narrow-tool vs. open-LLM distinction; +automation-bias / +deskilling complications
- [fda-510k-pathway](concepts/fda-510k-pathway.md) — dominant U.S. regulatory route; 1,357 devices; 76.6% radiology; <1% report patient outcomes, 91% lack bias assessments
- [medical-imaging-ai](concepts/medical-imaging-ai.md) — imaging AI hub; 2025 prospective RCTs (Vara MG mammo, Brainomix 360 stroke, EyeFM ophth); illusion of multimodal readiness
- [ambient-ai-scribes](concepts/ambient-ai-scribes.md) — largest 2025 deployment; first two RCTs (Afshar/Lukac NEJM AI Nov 2025); subjective burnout-down, objective ~20s/note
- [llm-clinical-reasoning](concepts/llm-clinical-reasoning.md) — o1-preview vs. physicians; primary citation Brodeur ArXiv Jul 2025; suboptimal-teaming finding; AMIE/Dr.CaBot context
- [agentic-clinical-ai](concepts/agentic-clinical-ai.md) — multi-agent gains 7–60%; MAC, TrialGenie, MAI-DxO; **optimization paradox** caveat; multi-agent safety advantage in NOHARM
- [ai-hallucination-medical](concepts/ai-hallucination-medical.md) — KaBLE, AA-Omniscience, NOHARM 22%/77%-omission, MetaMedQA, CRAFT-MD, NOTA, SourceCheckup, illusion of multimodal readiness
- [automation-bias-medical-ai](concepts/automation-bias-medical-ai.md) — Qazi medRxiv Sept 2025: AI-trained physicians drop 85% → 73% with planted erroneous LLM output
- [ai-deskilling](concepts/ai-deskilling.md) — Budzyn Lancet GH Oct 2025: colonoscopy ADR 28.4% → 22.4% three months after AI exposure (OR 0.69)
- [noharm](concepts/noharm.md) — ARISE's safety benchmark; 100 specialist consults, 31 LLMs, **22% severe harm**, 77% errors of omission, MedQA correlates only R=0.61–0.64
- [healthbench](concepts/healthbench.md) — OpenAI; 5,000 conversations × 262 physicians × 60 countries × 48,562 rubric criteria; GPT-3.5 16% → o3 60%
- [medhelm](concepts/medhelm.md) — Stanford 35-benchmark suite; 12 use real EHR data; LLMs strongest on documentation, weakest on admin/workflow
- [medagentbench](concepts/medagentbench.md) — Stanford FHIR-EHR benchmark; 300 query+action tasks; Claude 3.5 Sonnet 70% (queries 85%, actions 54%)
- [sdbench](concepts/sdbench.md) — Microsoft AI Sequential Diagnosis Benchmark; 304 NEJM CPCs as stepwise encounters; Gatekeeper + synthetic findings + Judge methodology
- [protein-language-models](concepts/protein-language-models.md) — 2025 shift from scaling (ESM3) to specialization (MSAPairformer); ProteinGym
- [cofolding-models](concepts/cofolding-models.md) — AlphaFold 3 lineage; FoldBench; data-not-scale bottleneck; commercially permissive open replications
- [digital-twins-medicine](concepts/digital-twins-medicine.md) — NASEM definition (only 12.1% of studies satisfy); Twin Health diabetes RCT

## Entities
- [mai-dxo](entities/mai-dxo.md) — Microsoft AI Diagnostic Orchestrator; 80–85.5% on NEJM CPCs vs ~20% physicians, 70% cost reduction; primary citation Nori/Horvitz ArXiv 2506.22405
- [amie](entities/amie.md) — Google's Articulate Medical Intelligence Explorer; non-inferior to PCPs across multi-visit, multimodal, dialogue evaluations
- [ai-consult-penda](entities/ai-consult-penda.md) — Penda Health × OpenAI Kenya deployment; **first prospective LLM copilot in real care**; 39,849 visits, 16% diagnostic-error reduction
- [delphi-2m](entities/delphi-2m.md) — UK Biobank GPT-2-based generative transformer; AUC 0.76 next-disease prediction; 20-year trajectory simulation; medical-event tokenization paradigm
- [comet](entities/comet.md) — Epic Cosmos Medical Event Transformer; 118M patients / 115B events; largest medical foundation model by event count; available Feb 2026
- [echonext](entities/echonext.md) — ECG-based deep learning for structural heart disease; trained on 1.2M ECG-echo pairs; outperforms cardiologists 77% vs 64%
- [present-shd](entities/present-shd.md) — SHD detection from ECG *images including phone photos*; 261k ECG images; AUROC 0.85–0.90; opportunistic screening
- [abridge](entities/abridge.md) — leading ambient AI scribe platform; 150+ health systems; multi-site outcomes
- [trews](entities/trews.md) — Targeted Real-time Early Warning System (Johns Hopkins/Bayesian Health); 18.7% sepsis mortality reduction across 13 Cleveland Clinic hospitals
- [arise-network](entities/arise-network.md) — Stanford-Harvard meta-evaluator; publishes *State of Clinical AI Report* and maintains [noharm](concepts/noharm.md) benchmark
- [eric-horvitz](entities/eric-horvitz.md) — Microsoft CSO and connecting figure across MAI-DxO, ARISE, collaborative-AI design, and foundational Bayesian-decision-theory diagnostic-AI work back to Pathfinder (1992)
- [evo-2](entities/evo-2.md) — 40B-param genomic foundation model (Arc Institute); outperformed by 200M GPN-Star on variant effect
- [alphafold-3](entities/alphafold-3.md) — Google DeepMind cofolding flagship; 64.9% on FoldBench, still leading

## Comparisons
*(none yet — created when query results are filed back)*

## Awaiting ingest (in `raw/`)
- `raw/claudes-constitution_webPDF_26-02.02a.pdf` — Anthropic, Claude's Constitution *(relevance to medical diagnostics: indirect; deployment-safety / refusal behavior in clinical contexts)*
- `raw/1426.pdf`, `raw/2749.pdf` — 1984/1994 corneal-topography papers; out of wiki scope.

## Suggested next sources to fetch
*(see [overview](overview.md) § Open questions for full list)*
- Bedi/Shah JAMA Jan 2025 — primary source for the "5%" stat
- NOHARM (Wu/Goh ArXiv Dec 2025) primary paper
- Brodeur Buckley Manrai Rodman ArXiv Jul 2025 — primary o1-preview / NEJM-CPC / ED paper
- TREWS / COMPOSER primary publications
- Recent NEJM AI / JAMA Network Open issues with prospective imaging trial reports
- Stanford FURM framework documentation
