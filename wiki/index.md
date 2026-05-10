---
type: index
updated: 2026-05-10
---

# Index

Content catalog for the AI-for-medical-diagnostics wiki. Updated on every ingest.

## Top-level
- [overview](overview.md) — evolving synthesis of AI for medical diagnostics; two-track field framing (strong-evidence narrow tools vs. capability-ahead-of-evidence open-ended AI)

## Sources
- [ai-index-2026](sources/ai-index-2026.md) — Stanford HAI, AI Index Report 2026 (April 2026, 425 pp). First edition with standalone Medicine and Science chapters.
- [llm-wiki](sources/llm-wiki.md) — meta-document describing the LLM-wiki pattern this project uses *(methodology, not domain content)*

## Concepts
- [clinical-validation](concepts/clinical-validation.md) — the central evidence-base tension; ARISE 5%/half-study finding; prospective trials; narrow-tool vs. open-LLM distinction
- [fda-510k-pathway](concepts/fda-510k-pathway.md) — dominant U.S. regulatory route; 1,357 cumulative AI/ML devices; 76.6% radiology; PCCPs under TPLC guidance
- [medical-imaging-ai](concepts/medical-imaging-ai.md) — hub for imaging AI: data scarcity, VLMs by specialty, prospective trials, cross-model benchmark gap
- [ambient-ai-scribes](concepts/ambient-ai-scribes.md) — largest 2025 clinical AI deployment category; multi-site outcomes evidence; constrained-workflow rationale
- [llm-clinical-reasoning](concepts/llm-clinical-reasoning.md) — Brodeur et al. NEJM cases; o1-preview vs. physicians; case-bench-vs-real-practice gap
- [agentic-clinical-ai](concepts/agentic-clinical-ai.md) — multi-agent diagnostic systems; 7–60% gains over single-agent baselines; MedAgentBench reality check at 69.7%
- [protein-language-models](concepts/protein-language-models.md) — 2025 shift from scaling (ESM3) to specialization (MSAPairformer); ProteinGym
- [cofolding-models](concepts/cofolding-models.md) — AlphaFold 3 lineage; FoldBench; data-not-scale bottleneck; commercially permissive open replications
- [digital-twins-medicine](concepts/digital-twins-medicine.md) — NASEM definition (only 12.1% of studies satisfy); Twin Health diabetes RCT
- [ai-hallucination-medical](concepts/ai-hallucination-medical.md) — KaBLE belief-vs-fact failure mode; AA-Omniscience health-domain rates; NOHARM benchmark

## Entities
- [mai-dxo](entities/mai-dxo.md) — Microsoft AI Diagnostic Orchestrator; 85.5% on NEJM cases vs. ~20% for 21 experienced physicians
- [abridge](entities/abridge.md) — leading ambient AI scribe platform; 150+ health systems; multi-site outcomes
- [trews](entities/trews.md) — Targeted Real-time Early Warning System (Johns Hopkins/Bayesian Health); 18.7% sepsis mortality reduction across 13 Cleveland Clinic hospitals
- [arise-network](entities/arise-network.md) — Stanford-Harvard meta-evaluator; *State of Clinical AI Report* (Jan 2026)
- [evo-2](entities/evo-2.md) — 40B-param genomic foundation model (Arc Institute); outperformed by 200M GPN-Star on variant effect
- [alphafold-3](entities/alphafold-3.md) — Google DeepMind cofolding flagship; 64.9% on FoldBench, still leading

## Comparisons
*(none yet — created when query results are filed back)*

## Awaiting ingest (in `raw/`)
- `raw/claudes-constitution_webPDF_26-02.02a.pdf` — Anthropic, Claude's Constitution *(relevance to medical diagnostics: indirect; deployment-safety / refusal behavior in clinical contexts)*

## Suggested next sources to fetch
*(see [overview](overview.md) § Open questions for full list)*
- ARISE *State of Clinical AI Report* (Jan 2026) — primary
- Microsoft MAI-DxO primary publication
- TREWS / COMPOSER primary publications
- Recent NEJM AI / JAMA Network Open issues with prospective imaging trial reports (MASAI, NOTIFY-1, NOTIFY-EXTEND)
- Stanford FURM framework documentation
