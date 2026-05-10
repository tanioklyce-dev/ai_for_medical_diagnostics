---
type: source
title: AI Index Report 2026 (Stanford HAI)
authors: [Sha Sajadieh, Loredana Fattorini, Raymond Perrault, Vanessa Parli, Lapo Santarlasci, Juan Pava, Nestor Maslej, Russ Altman, Erik Brynjolfsson, Carla Brodley, Jack Clark, Virginia Dignum, Vipin Kumar, James Landay, Terah Lyons, James Manyika, Juan Carlos Niebles, Yoav Shoham, Elham Tabassi, Russell Wald, Toby Walsh, Dan Weld]
published: 2026-04
ingested: 2026-05-10
source_path: raw/ai_index_report_2026.pdf
pages: 425
license: CC BY-ND 4.0
tags: [broad-survey, source-of-record, stanford-hai]
---

# AI Index Report 2026

> The 9th annual AI Index, published by Stanford HAI. **First edition with standalone chapters on AI in Science (Ch. 5) and AI in Medicine (Ch. 6)** — explicitly added to reflect AI's growing impact in these domains. The Medicine chapter (~33 pages, p. 255–287) is the spine of this wiki for now; the Science chapter contributes upstream biomedical context; selected Responsible AI material (Ch. 3) covers cross-cutting safety/hallucination/incident data.

## Summary

The 2026 AI Index argues that AI is now scaling faster than the systems built around it — governance, evaluation, data infrastructure — can adapt. In medicine specifically, the report frames 2025 as the year clinical AI moved from *pilot programs to enterprise-scale deployments*, while the underlying evidence base remained thin: a Stanford-Harvard ARISE Network review of 500+ clinical AI studies found that nearly half relied on exam-style questions and **only 5% used real clinical data**. The diagnostic AI device market accelerated dramatically — the FDA had cleared **1,357 cumulative AI/ML devices from 693 companies across 17 specialties** by Dec 2025, with 246 of those clearances landing in 2025 alone. Radiology accounts for 76.6% (1,039 devices); cardiology, neurology, anesthesiology, and gastroenterology are growing. But cross-model imaging benchmarks are still missing, and prospective clinical trials, while growing 28.5% YoY (417→536), remain a fraction of total publication output.

The chapter's most provocative findings come from LLM clinical reasoning. Brodeur et al. (2025) showed OpenAI's o1-preview correctly placing the right diagnosis in its differential in 78/80 NEJM cases (52% top-1), achieving a perfect IDEA score of 78/80 vs. 47/80 for GPT-4, 28/80 for attendings, and 16/80 for residents. Microsoft's **AI Diagnostic Orchestrator (MAI-DxO)** paired with OpenAI o3 scored 85.5% on diagnostically challenging NEJM cases, vs. ~20% for 21 practicing physicians with 5–20 years of experience working under comparable conditions. Multi-agent gains over single-agent baselines run 7% to over 60%. The report is careful to caveat these as isolated cognitive evaluations — whether they translate to better real-world outcomes is the next open question, and on more deployment-realistic benchmarks (MedAgentBench, 300 EHR-derived tasks) the best model still tops out at 69.7%.

The biggest deployed-AI story of 2025 is **ambient AI scribes** (see [[ambient-ai-scribes]]). Abridge alone expanded from ~100 to 150+ health systems, with Kaiser Permanente deploying across 40 hospitals and 600+ medical offices. Documented outcomes were consistent: Sharp HealthCare reported 83% reduction in note-writing effort, Stanford's prospective study (n=48, JAMIA Feb 2025) showed statistically significant burnout reductions and 20-min savings per half day, Northwestern reported 11.3 additional patients/month and 112% ROI. Two AI sepsis prediction systems also reported large-scale prospective deployment outcomes: **TREWS** (Johns Hopkins / Bayesian Health, 13 Cleveland Clinic hospitals) reduced sepsis mortality 18.7% relative; **COMPOSER** (UCSD, 6,217 admissions) reduced sepsis mortality 17%. The author's framing matters: scribes and sepsis alerts work *because they operate in constrained workflows under clinician oversight*, while the NOHARM benchmark found general-purpose LLMs produce 11.8–14.6 severely harmful recommendations per 100 open-ended clinical cases (76.6% errors of omission).

Upstream of clinical care, the **biomedical foundation model wave** continued, with a notable shift from scaling to specialization. Smaller, curated models beat larger general ones: MSAPairformer (111M parameters) surpassed previous SOTA on ProteinGym, and GPN-Star (200M) outperformed Evo 2 (40B) on variant effect prediction. AlphaFold 3-style cofolding models converged at ~370M–923M parameters, with FoldBench accuracy plateauing — the bottleneck shifted to data sources and "distilled" datasets of AI-predicted structures, not parameter count. Virtual cell models (Evo 2, STATE, AlphaGenome) emerged as a new frontier. Agentic biomedical discovery systems (Robin, STELLA, Biomni, The Virtual Lab) showed early but real wins, with Robin identifying ripasudil as a novel candidate for dry age-related macular degeneration.

The Responsible AI chapter contributes important medical-relevant signals: documented AI incidents rose from 233 (2024) to 362 (2025); hallucination rates across 26 top models on AA-Omniscience range 22–94%, with explicit per-domain tracking including health; and the **KaBLE benchmark** showed GPT-4o accuracy collapsing from 98.2% on third-person true facts to **64.4% when a false claim is framed as the user's first-person belief** — a directly diagnostic-relevant failure mode where a model could reinforce a patient's mistaken belief.

## Key claims and findings (by section)

### Top takeaways (front matter, p. 9–11)
- **#11**: AI models for science can outperform human scientists, but bigger models don't always perform better. MSAPairformer (111M) beat ProteinGym SOTA; GPN-Star (200M) > Evo 2 (40B).
- **#12**: AI is transforming clinical care, but rigorous evidence remains limited. Ambient AI scribes scaled; 5% of 500+ clinical AI studies used real clinical data.
- **#15**: 50-point gap between AI experts and the public on AI's positive impact, including on medical care.

### Chapter 6 — Medicine (p. 255–287)

**6.1 The Central Dogma (molecular/biological AI):**
- AI-driven protein research grew 71% (2,259 → 3,855 papers, 2024–2025); protein-drug interactions are the largest share (54.4%).
- AI for drug discovery: 431 publications (2018) → 3,311 (2025).
- See [[protein-language-models]], [[cofolding-models]] for model-family detail. Virtual cell models: [[evo-2]], STATE, [[alphafold-3]] (cofolding flagship), AlphaGenome, GPN-Star.
- Agentic biomedical discovery: Robin (identified ripasudil as candidate for dry age-related macular degeneration), STELLA (autonomous bioinformatics agent), Biomni (Stanford, 25 subfields, 150 tools, 105 software packages, 59 databases), Agent Laboratory (AMD/Johns Hopkins, role-assigned multi-agent), The Virtual Lab (LLM PI orchestrating specialist agents — 92 SARS-CoV-2 nanobody designs).
- Multimodal biomedical AI publications: 2 (2021) → 462 (2025).

**6.2 Clinical Applications:**
- See [[medical-imaging-ai]] for full imaging-by-specialty treatment.
- Medical imaging training data ~100x smaller than general (MAIRA-2: 1.4M chest X-rays vs. DINOv3: 1.7B images).
- Prospective trials: 417 (2024) → 536 (2025), 28.5% YoY. Examples: MASAI (mammography RCT), NOTIFY-1/NOTIFY-EXTEND (early heart-disease detection on routine CT).
- LLM clinical reasoning: see [[llm-clinical-reasoning]] for Brodeur et al. NEJM data.
- AI agents in clinical medicine: see [[agentic-clinical-ai]]; key entity [[mai-dxo]].
- FDA pathway and device counts: see [[fda-510k-pathway]].
- Industry landscape (top FDA device counts 2016–2025): GE Healthcare 93, Siemens Healthineers 82, Shanghai United Imaging 38, Philips 36, Canon 35, Aidoc 30, Samsung 20, iSchemaView 20, Hyperfine 12, Viz.ai 12.
- Enterprise deployments: see [[ambient-ai-scribes]] (key entity [[abridge]]); sepsis prediction ([[trews]], COMPOSER).
- Generative AI in EHRs: ChatEHR (Stanford, 23,000 sessions, 1,075 trained users), OpenEvidence (40% U.S. physician adoption).
- Evidence gaps and governance: [[arise-network]] (Stanford-Harvard, *State of Clinical AI Report* Jan 2026), NOHARM benchmark, Stanford Health Care's FURM framework, GUIDE-AI Lab. See [[clinical-validation]].
- Digital twins: see [[digital-twins-medicine]]; 12.1% of 149 studies satisfied NASEM definition; Twin Health diabetes RCT (n=150, 71% achieved HbA1c <6.5%).

**6.3 Patient Engagement:**
- AI Overviews appear on 84–92% of health-related Google searches (highest for symptom and common-health queries at 92%).
- Patient perception publications: 9 (2020) → 102 (2025).
- Mello et al. (2025) framework: consent vs. notification vs. neither, based on harm risk. Most-studied specialties (after general healthcare): internal medicine, radiology, OB/Gyn, oncology, psychiatry.

**6.4 Ethical Considerations:**
- 43.4% of medical AI publications discussed ethics in 2025 (up from 37.1% in 2024). Total medical AI publications in 2025: 5,477 (up from 3,000).
- Topic distribution: governance 1,228 > algorithmic 896 > societal 874.
- **Biosecurity gap**: only 14 publications in 2025 — relevant to dual-use concerns despite policy attention.
- Global health distinct: equity / justice / accessibility (societal) ranked above governance and algorithmic. Sub-Saharan Africa, Latin America, Oceania each <5 publications.

### Chapter 5 — Science, biomedical-relevant pieces (p. 231–250)
- AI-related publications in life sciences: ~29,000 (2025), 27–28% YoY growth; 6.48% of all life sciences output mentions AI (up from <1% in 2010).
- Notable life-sciences foundation models added in this section beyond Ch. 6: AlphaGenome (DeepMind), BioCLIP 2 (OSU/Smithsonian), CellFM (Sun Yat-sen, 800M params, 100M cells), BioLab (Princeton/BioMap multi-agent system with experimentally validated antibody designs), ProteinTalks (Westlake).
- Agents: BCI-Agent (Harvard/MIT/Broad — autonomous neuronal cell-type classification), BioAgents (Berkeley/Microsoft/UCSF).
- Benchmarks: BixBench (50+ bioinformatics scenarios, GPT-4o & Claude 3.5 Sonnet ~17% accuracy), BioML-bench (first end-to-end biomedical ML eval), CGBench (Stanford, clinical genetics interpretation, reasoning models excel but hallucination gaps remain).
- Dataset of note: OpenGenome2 (9.3 trillion DNA base pairs, training corpus for Evo 2).

### Chapter 3 — Responsible AI, medically-relevant pieces (p. 126–146)
- **AI Incident Database**: 362 incidents in 2025 (up from 233). OECD AIM 6-month moving average: 326; peak 435 (Jan 2026). Coverage skews English-language and high-visibility.
- **AA-Omniscience**: hallucination 22–94% across 26 models. Per-domain breakout includes Health — variation by model is large. Best (least hallucinatory): Grok 4.20 Beta 0305 (22%), Claude 4.5 Haiku (26%), MiMo-V2-Pro (30%).
- **HHEM (Vectara)**: hallucination 1.8–5.4% on document summarization (CNN/Daily Mail).
- **KaBLE benchmark** (Suzgun et al., 2025): 13,000 questions across 13 tasks. GPT-4o accuracy on third-person true facts 98.2% → 64.4% on first-person false beliefs. DeepSeek R1: >90% → 14.4%. The report explicitly flags this as a medical-diagnostic failure mode: "a model used to support a medical diagnosis based on a patient's mistaken belief, as opposed to an established fact, could reinforce an inaccurate diagnosis and treatment plan." See [[ai-hallucination-medical]].
- **Tradeoff finding**: training techniques aimed at improving one RAI dimension (e.g., safety) consistently degrade another (e.g., accuracy). Important caveat for medical AI safety tuning.

## Pages of relevance (PDF page → printed page is offset by 1; cite by printed)

| Topic | Printed pages |
|---|---|
| Top takeaways | 9–11 |
| Ch. 5 biomedical sections (5.2 Biological & Life Sciences) | 242–246 |
| Ch. 6 — Medicine (full chapter) | 255–287 |
| 6.1 Central Dogma (protein, cofolding, virtual cell, agentic) | 258–268 |
| 6.2 Clinical Applications (imaging, LLM reasoning, agents, FDA) | 269–279 |
| Enterprise deployments (scribes, sepsis, gen AI EHR) | 276–278 |
| 6.3 Patient Engagement | 280–283 |
| 6.4 Ethical Considerations | 284–287 |
| Ch. 3 — Responsible AI (highlights through §3.3) | 127–146 |
| AA-Omniscience domain breakdown (incl. Health) | 137 |
| KaBLE belief-vs-fact (medically framed) | 138 |

## Notes

- The report is **bibliometric and survey-driven**, not a primary-source clinical study. Most of the medical-evidence claims are *meta-claims about the literature* (citation counts, benchmark coverage) rather than original effect estimates. The TREWS, COMPOSER, Twin Health, MASAI, NOTIFY trials cited are summarized — drill into the underlying papers for primary data.
- The Medicine chapter draws heavily on **RAISE Health (Stanford)** for many of its figures. RAISE Health is also a "Analytics & Research Partner" (cover material p. 6) — worth noting for source-independence considerations.
- "FDA-cleared" ≠ "deployed." Industry-landscape data shows market is concentrated at the top but fragmented overall: of 626 companies with at least one cleared device, the large majority hold only 1–2.
- The report flags but does not resolve the **belief-vs-fact failure mode** for medical LLMs (KaBLE). This is a high-priority follow-up topic — needs primary-paper ingestion to ground.
- **Conflicts to flag in future ingests**: The 5% real-clinical-data finding (ARISE) is widely cited; verify against the primary Stanford-Harvard ARISE *State of Clinical AI Report* if/when it's added to `raw/`. Also: the MAI-DxO 85.5% vs. 20% physician comparison should be checked against Microsoft's primary publication — the 5–20 years experience and "comparable conditions" framing matters a lot.

## Citation

Sha Sajadieh, Loredana Fattorini, Raymond Perrault, et al. *The AI Index 2026 Annual Report*, AI Index Steering Committee, Institute for Human-Centered AI, Stanford University, Stanford, CA, April 2026.
