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

## [2026-05-10] ingest | Sequential Diagnosis with Language Models (MAI-DxO primary)
Source: `raw/mai_dxo_sequential_diagnosis_2025.pdf` (31 pp, ArXiv 2506.22405v2, Nori, Daswani, ..., Horvitz et al., Microsoft AI, Jul 2025). URL: <https://arxiv.org/abs/2506.22405>. Filed as [mai-dxo-sequential-diagnosis-2025](sources/mai-dxo-sequential-diagnosis-2025.md).
**Read scope**: full paper (31 pages: abstract, intro, SDBench methodology, MAI-DxO architecture, physician comparison, results across 10 base models, discussion, limitations, references, appendices).
**Pages created (3)**:
- Source page: [mai-dxo-sequential-diagnosis-2025](sources/mai-dxo-sequential-diagnosis-2025.md)
- Concept: [sdbench](concepts/sdbench.md) — separates the benchmark methodology (Gatekeeper + synthetic findings + Judge rubric) from the orchestrator
- Entity: [eric-horvitz](entities/eric-horvitz.md) — load-bearing connecting figure across MAI-DxO, ARISE, collaborative-AI work, and foundational Bayesian decision theory dating to Pathfinder (1992)
**Pages updated (4)**: [mai-dxo](entities/mai-dxo.md) (major rewrite — full 5-agent architecture, 5 configuration variants, +11pp boost across 10 models, Cohen's κ validity, stated limitations), [agentic-clinical-ai](concepts/agentic-clinical-ai.md) (Chain of Debate pattern, supervising-coordination role from MAC framework), [llm-clinical-reasoning](concepts/llm-clinical-reasoning.md) (single-LLM baseline table on SDBench), [clinical-validation](concepts/clinical-validation.md) (SDBench as middle-layer methodology; explicit note about physicians-forbidden-from-resources constraint in case-bench studies).
**Citation precedence**: this is now the **primary** for MAI-DxO claims. ARISE and AI Index are secondary on MAI-DxO specifics.
**Notable findings (beyond what ARISE summarized)**:
- Architectural specificity: five named virtual physicians (Hypothesis, Test-Chooser, Challenger, Stewardship, Checklist) deliberating via "Chain of Debate." Confirms Bayesian-decision-theory lineage back to Horvitz's 1980s–90s work.
- +11pp average accuracy gain across 10 base models (Claude 4 Sonnet/Opus, Gemini 2.5 Flash/Pro, GPT-4.1, o3, o4-mini, Grok-3, Llama 4 Maverick, DeepSeek-R1). All gains *p* < 0.005.
- Cohen's κ = 0.70 Judge-vs-physician (vs 0.87 human-vs-human). Physicians judged Judge "overly strict" in 4 of 5 disagreements — true accuracy likely slightly higher than reported.
- Held-out test set methodology (56 most recent cases 2024–2025) shows gains robust against memorization.
- The "instructive case" (hand-sanitizer alcohol withdrawal): off-shelf o3 fixated on antibiotic toxicity, MAI-DxO's Dr. Hypothesis flagged toxin exposures in round 1, panel asked about hand sanitizer → correct diagnosis at $795 vs o3's wrong diagnosis at $3,431. *This is the qualitative mechanism the architecture buys you.*
- Physicians were **explicitly forbidden** from external resources (search, LLMs, EHR, colleagues). The paper acknowledges in Sec 5.3 this is "not reflective of real clinical practice." The 19.9% physician baseline is a constrained floor.
- SDBench may matter beyond MAI-DxO: methodology is reusable, and the paper explicitly states intent to submit for peer review and explore public release.

## [2026-05-10] ingest | Ogut MDPI clinical AI review
Source: `raw/clinpract-15-00169.pdf` (20 pp, MDPI *Clinics and Practice* 2025, 15, 169, Eren Ogut single-author PRISMA-style review of 150 studies). DOI: 10.3390/clinpract15090169. Filed as [ogut-ai-clinical-medicine-2025](sources/ogut-ai-clinical-medicine-2025.md).
**Read scope**: full paper.
**Pages created (1)**: source page only — quality-over-coverage judgment. Review confirms but doesn't add much beyond the ARISE / AI Index narrative; methodological caveats include simulated p-values (paper's own term), no formal risk-of-bias assessment, single-author MDPI publication, and disclosed ChatGPT-assisted manuscript preparation.
**Pages updated (2)**: [clinical-validation](concepts/clinical-validation.md) (Vasey 2021 ML-CDSS systematic review primary citation + CONSORT-AI / SPIRIT-AI reporting standards), [medical-imaging-ai](concepts/medical-imaging-ai.md) (2016–2021 landmark imaging-AI citations — Rodriguez-Ruiz 2019, Mayo 2019, Gulshan 2016, Försch 2021, Attia 2019).
**Most useful contribution**: Vasey/JAMA Network Open 2021 — systematic review of 37 ML-CDSS studies finding ~half showed improvement, ~half no change, no clear improvement in real-world simulating studies. Strongest pre-2025 primary citation for the CDSS-evidence-base gap; complements Bedi/Shah JAMA Jan 2025 "5%" stat in [clinical-validation](concepts/clinical-validation.md).
**Citation precedence**: prefer ARISE 2026 over Ogut for any synthesis claim; use Ogut as a citation map to underlying primary literature (Vasey, Försch, Mayo, Gulshan, Rajkomar, Attia, CONSORT-AI).

## [2026-05-10] ingest | Stephen Klyce ophthalmology AI history (1984 + 1994 IOVS papers)
Sources: `raw/1426.pdf` (Klyce IOVS Dec 1984, 10 pp, *Computer-Assisted Corneal Topography*) and `raw/2749.pdf` (Maeda, Klyce, Smolek, Thompson IOVS May 1994, 9 pp, *Automated Keratoconus Screening With Corneal Topography Analysis*). Filed as [klyce-computer-assisted-corneal-topography-1984](sources/klyce-computer-assisted-corneal-topography-1984.md) and [maeda-klyce-keratoconus-screening-1994](sources/maeda-klyce-keratoconus-screening-1994.md). User framing: pioneer contributions to medical AI in ophthalmology; treat factually and with web-supported research depth (not just papers in `raw/`).
**Read scope**: both papers in full.
**Pages created (4)**:
- Source pages (2): Klyce 1984 and Maeda/Klyce/Smolek/Thompson 1994.
- Entity: [stephen-klyce](entities/stephen-klyce.md) — biographical details from web research (Yale PhD 1971, Stanford 1972-79, LSU 1979-2008, Mount Sinai 2008-present; FARVO; 11 named awards including 2009 ARVO Gold Fellow, 2010 ISRS/AAO Barraquer, 2016 J. Refractive Surgery Waring Medal).
- Concept: [keratoconus-screening-ai](concepts/keratoconus-screening-ai.md) — four-rung lineage from 1984 to 2025 (quantitative imaging → expert system → neural network → deep learning), with continued use of KPI/DSI/OSI/CSI/SAI/IAI indices as engineered features in modern deep-learning systems.
**Pages updated (3)**: [medical-imaging-ai](concepts/medical-imaging-ai.md) (pre-deep-learning ophthalmology lineage section), [eric-horvitz](entities/eric-horvitz.md) (parallel-specialty contemporary cross-link), [overview](overview.md) (historical-depth section).
**Notable findings**:
- Klyce 1984 explicitly sketches an "expert system within the realm of current technology" — automated `diagnose` module + continuously-learning patient + AI diagnosis `learn` database. 1984 statement of intent for what we now call closed-loop / continuously-learning clinical AI.
- Maeda/Klyce/Smolek/Thompson 1994 is **the first explicitly-AI-labeled** ophthalmology screening system in this lineage. Discriminant analysis → KPI → Pascal binary decision tree → 89% sens / 99% spec / 96% acc on validation; statistically significant gain over discriminant alone (McNemar p=0.016).
- Same expert-system wave as Pathfinder (1992, Heckerman/Horvitz/Nathwani — see [eric-horvitz](entities/eric-horvitz.md)) and MYCIN (1976). Klyce's keratoconus work is the **ophthalmology-specific** parallel.
- KPI, DSI, OSI, CSI, SAI, IAI, AA indices developed in 1994 remain standard inputs / baselines for modern deep-learning keratoconus systems — 30+ year survival of feature engineering, an unusual outcome in clinical AI.
- Klyce career: Yale PhD 1971 → Stanford 1972-79 → LSU 1979-2008 → Mount Sinai 2008-present; ~250 peer-reviewed publications; consultant for NIDEK, Smart EyeDeas, Oculus (commercial videokeratographer vendors).
**Cited but not yet in `raw/`**: Maeda/Klyce/Smolek 1995 IOVS neural-network paper (PubMed 7775110); Smolek/Klyce 1997 IOVS neural-network systematic comparison (PubMed 9344352). Both would close the lineage from rule-based expert system → multilayer perceptron in this same group.
