---
type: log
---

# Log

Chronological record of wiki activity. Append-only, newest at the bottom.
Each entry starts with `## [YYYY-MM-DD] <op> | <subject>` so it's grep-parseable:
`grep "^## \[" wiki/log.md | tail -5`.

## [2026-05-10] bootstrap | wiki initialized
Created wiki structure and schema for the AI-for-medical-diagnostics research project.
- Schema: `CLAUDE.md`
- Created: `wiki/index.md`, `wiki/log.md`, `wiki/overview.md` (stub), `wiki/sources/` directory.
- Scope confirmed with human: AI for medical diagnostics, research deep-dive. One-at-a-time ingest workflow.

## [2026-05-10] ingest | LLM Wiki (meta-document)
Source: `raw/llm-wiki.md`. Filed as [llm-wiki](sources/llm-wiki.md).
This is the pattern blueprint — methodology, not domain content. No entity/concept pages created from it. Conventions chosen during this ingest are codified in `CLAUDE.md`.

## [2026-05-10] ingest | AI Index Report 2026 (Stanford HAI)
Source: `raw/ai_index_report_2026.pdf` (425 pp). Filed as [ai-index-2026](sources/ai-index-2026.md).
**Read scope**: Medicine chapter in full (p. 255–287), Science chapter biomedical sections (p. 232–250), Responsible AI chapter sections 3.1–3.3 incl. KaBLE, AA-Omniscience, AIID (p. 127–146). Skipped: Education, Economy, Policy/Governance, Public Opinion, R&D — out of scope for this wiki.
**Pages created (17)**:
- Source page: [ai-index-2026](sources/ai-index-2026.md)
- Concepts (10): [clinical-validation](concepts/clinical-validation.md), [fda-510k-pathway](concepts/fda-510k-pathway.md), [medical-imaging-ai](concepts/medical-imaging-ai.md), [ambient-ai-scribes](concepts/ambient-ai-scribes.md), [llm-clinical-reasoning](concepts/llm-clinical-reasoning.md), [agentic-clinical-ai](concepts/agentic-clinical-ai.md), [protein-language-models](concepts/protein-language-models.md), [cofolding-models](concepts/cofolding-models.md), [digital-twins-medicine](concepts/digital-twins-medicine.md), [ai-hallucination-medical](concepts/ai-hallucination-medical.md)
- Entities (6): [mai-dxo](entities/mai-dxo.md), [abridge](entities/abridge.md), [trews](entities/trews.md), [arise-network](entities/arise-network.md), [evo-2](entities/evo-2.md), [alphafold-3](entities/alphafold-3.md)
**Pages updated**: [overview](overview.md) (replaced stub with two-track-field synthesis; five-axis structure), `wiki/index.md` (new entries for all created pages).
**Notable findings to track in future sources**:
- ARISE Network 5%-real-clinical-data finding (cite the primary report when ingested).
- MAI-DxO 85.5% vs. ~20% physician comparison — case-bench, not real-world; verify Microsoft primary publication.
- KaBLE belief-vs-fact failure mode is a directly diagnostic-relevant LLM risk worth a follow-up source.
- The narrow-tool-vs-open-LLM distinction is the load-bearing organizing principle from this source.

## [2026-05-10] ingest | ARISE State of Clinical AI Report 2026
Source: `raw/arise_state_of_clinical_ai_2026.pdf` (130 slides, January 2026, ARISE Network — Stanford / Harvard / Beth Israel Deaconess). URL: <https://arise-ai.org/report>. Filed as [arise-state-of-clinical-ai-2026](sources/arise-state-of-clinical-ai-2026.md).
**Read scope**: full report (130 slides). Six sections — Model Performance, Benchmarks & Evaluations, Foundational Methods, AI in Clinical Workflows, Patient-Facing AI, Applied AI & Demos — plus 10 Predictions, Disclosures, Acknowledgements.
**Pages created (12)**:
- Source page: [arise-state-of-clinical-ai-2026](sources/arise-state-of-clinical-ai-2026.md)
- Entities (5 new): [amie](entities/amie.md), [ai-consult-penda](entities/ai-consult-penda.md), [delphi-2m](entities/delphi-2m.md), [comet](entities/comet.md), [echonext](entities/echonext.md), [present-shd](entities/present-shd.md)
- Concepts (6 new): [automation-bias-medical-ai](concepts/automation-bias-medical-ai.md), [ai-deskilling](concepts/ai-deskilling.md), [noharm](concepts/noharm.md), [healthbench](concepts/healthbench.md), [medhelm](concepts/medhelm.md), [medagentbench](concepts/medagentbench.md)
**Pages updated (9)**: [arise-network](entities/arise-network.md) (major expansion — this is *their* report), [mai-dxo](entities/mai-dxo.md) (primary citation Nori/Horvitz ArXiv 2506.22405; 70% cost reduction), [clinical-validation](concepts/clinical-validation.md) (Bedi/Shah JAMA Jan 2025 primary for "5%" stat; cross-cutting deployment hazards), [llm-clinical-reasoning](concepts/llm-clinical-reasoning.md) (Brodeur ArXiv primary; suboptimal teaming; AMIE/Dr.CaBot/SCT context), [agentic-clinical-ai](concepts/agentic-clinical-ai.md) (MAC/TrialGenie; optimization paradox; multi-agent safety advantage), [medical-imaging-ai](concepts/medical-imaging-ai.md) (2025 prospective RCTs; illusion of multimodal readiness), [ai-hallucination-medical](concepts/ai-hallucination-medical.md) (NOHARM full numbers; MetaMedQA, CRAFT-MD, NOTA, SourceCheckup, illusion of readiness, fine-tuning fragility), [ambient-ai-scribes](concepts/ambient-ai-scribes.md) (first RCTs Afshar/Lukac; AI message routing), [fda-510k-pathway](concepts/fda-510k-pathway.md) (slide-5 device-summary deficiencies primary).
**Schema updates**: added `url:` frontmatter field to source page convention in `CLAUDE.md`; back-filled [ai-index-2026](sources/ai-index-2026.md) with both `source_path` (raw/) and `url`.
**Citation precedence**: prefer ARISE as primary for clinical-AI claims; AI Index remains primary for the broader Medicine/Science/RAI cross-domain framing.
**Notable findings**:
- "5% real clinical data" stat now has a primary citation (Bedi/Shah JAMA Jan 2025).
- MAI-DxO numbers refined: 80% accuracy (slide 45) / 85.5% max-accuracy config; 70% cost reduction at cost-optimized config.
- NOHARM headline: 22% severe harm across 31 LLMs; 77% errors of omission; MedQA correlates only R=0.61–0.64.
- The "fundamental theorem of medical informatics" (human + AI > each alone) does *not* always hold — Goh/Chen GPT-4 RCT shows physicians + GPT-4 ≈ GPT-4 alone. Workflow design matters.
- Penda Health AI Consult: first prospective LLM-copilot deployment in real care (39,849 visits, 16% diagnostic-error reduction).
- Two new deployment-safety concerns now have hard 2025 evidence: [automation-bias-medical-ai](concepts/automation-bias-medical-ai.md) (Qazi 85% → 73%) and [ai-deskilling](concepts/ai-deskilling.md) (Budzyn ADR 28% → 22%).
