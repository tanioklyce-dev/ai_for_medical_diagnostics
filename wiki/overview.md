---
type: overview
title: AI for Medical Diagnostics — Overview
added: 2026-05-10
updated: 2026-05-10
sources: [sources/ai-index-2026.md, sources/arise-state-of-clinical-ai-2026.md, sources/mai-dxo-sequential-diagnosis-2025.md]
tags: [overview]
---

# AI for Medical Diagnostics — Overview

*Top-level synthesis. Updated 2026-05-10 after the [ARISE State of Clinical AI 2026](sources/arise-state-of-clinical-ai-2026.md) ingest, which adds primary citations for most claims previously summarized via the AI Index.*

## State of the field as of early 2026 (per [ai-index-2026](sources/ai-index-2026.md) + [arise-state-of-clinical-ai-2026](sources/arise-state-of-clinical-ai-2026.md))

Clinical AI moved from pilot programs to enterprise-scale deployments in 2025. The deployment story is real — multi-site outcomes evidence is accumulating for **narrow tools operating in constrained workflows under clinician oversight**. But the broader evidence base remains thin: the primary source for the famous "5%" critique is now ingested — *Bedi, Shah et al., JAMA Jan 2025*, n=519 LLM-eval studies 2022–2024 (95% used accuracy as primary metric, only 5% used real patient data, <0.5% studied admin/billing/prescription tasks).

The field is bifurcating along this evidence axis:

- **Strong evidence track**: ambient scribes, sepsis prediction, narrow imaging triage tools — clinician-in-loop, well-defined input/output, multi-site outcomes papers.
- **Capability-ahead-of-evidence track**: open-ended LLM clinical reasoning, multi-agent diagnostic systems, foundation models for medical imaging — strong benchmark performance, thin real-world validation, hallucination/factuality concerns.

## Five organizing axes (entry points to the wiki)

### 1. The evidence-validation axis
- **[clinical-validation](concepts/clinical-validation.md)** — the central tension. ARISE 5%/half-study finding. Prospective trials growing 28.5% YoY but still small relative to publication volume.
- **[arise-network](entities/arise-network.md)** — meta-evaluator publishing the *State of Clinical AI Report*.
- **[fda-510k-pathway](concepts/fda-510k-pathway.md)** — the regulatory substrate; substantial-equivalence-not-RCT model; 1,357 cumulative cleared devices.

### 2. The diagnostic-modality axis
- **[medical-imaging-ai](concepts/medical-imaging-ai.md)** — 76.6% of cleared devices, but data ~100x smaller than general; cross-model benchmarking still weak. ARISE adds 2025 primary citations for prospective imaging RCTs: Vara MG mammography (17.6% increase in detection without recall tax), Brainomix 360 stroke (EVT rates doubled across 26 NHS hospitals), EyeFM (75 → 92% diagnosis with AI assistance), AI-ECG cirrhosis screening (doubled new diagnoses).
- ECG screening hub: [echonext](entities/echonext.md) (1.2M ECG-echo pairs) and [present-shd](entities/present-shd.md) (works on phone photos) — opportunistic SHD screening from cheap, ubiquitous data.

### 3. The reasoning / agentic axis
- **[llm-clinical-reasoning](concepts/llm-clinical-reasoning.md)** — single-LLM benchmark performance now exceeds physician case-bench scores (o1-preview NEJM Healer: 78/80 vs. attendings 28/80; management reasoning 86% vs. 34%; primary citation: Brodeur ArXiv Jul 2025).
- **[agentic-clinical-ai](concepts/agentic-clinical-ai.md)** — multi-agent systems gain 7–60% over single-agent baselines. Critical caveat from ARISE: the **optimization paradox** (Bedi/Shah ArXiv Jun 2025) shows that "best-of-breed" multi-agent systems can perform *worse* than less-optimized ones because of breakdowns in inter-agent information flow. End-to-end validation matters more than component selection.
- **[mai-dxo](entities/mai-dxo.md)** — flagship: 80–85.5% on NEJM cases vs. ~20% for 21 experienced physicians, plus a 70% cost reduction with cost-optimized configuration.
- **[amie](entities/amie.md)** — Google's multimodal-and-multi-visit counterpart, non-inferior to PCPs across simulated dialogues.
- All gated by the case-bench-vs-real-practice translation problem — and complicated by ARISE's "**fundamental theorem of medical informatics doesn't always hold**" finding (physician + AI ≈ AI alone in the Goh/Chen GPT-4 RCT; collaborative interface design matters).

### 4. The deployed-clinical-AI axis
- **[ambient-ai-scribes](concepts/ambient-ai-scribes.md)** — biggest 2025 deployment story; **[abridge](entities/abridge.md)** at 150+ health systems. First two RCTs (Afshar/Lukac NEJM AI Nov 2025) confirm: subjective burnout reduction is real (Olson JAMA Network Open Oct 2025: 52% → 39%, OR 0.26), objective time savings ~20 s/note. Productivity gains will require scope expansion to downstream workflow tasks.
- **[ai-consult-penda](entities/ai-consult-penda.md)** — *first prospective LLM-copilot deployment in real care.* Penda Health × OpenAI in Kenya, 39,849 visits across 15 sites, 16% diagnostic-error and 13% treatment-error reduction. Crosses the "narrow-tools-only have strong evidence" line.
- **[trews](entities/trews.md)** — sepsis early warning, 18.7% mortality reduction, 13 Cleveland Clinic hospitals.
- Brainomix 360 stroke (NHS, 26 hospitals, EVT doubled), Vara MG mammography (12 sites, 463k women), EyeFM RCT — case studies for the *strong evidence track* in narrow domain tools.

### 5. The biomedical-foundation-model axis
- **[protein-language-models](concepts/protein-language-models.md)** — 2025 shift from scaling (ESM3, 98B) to specialization (MSAPairformer, 111M, beats SOTA).
- **[cofolding-models](concepts/cofolding-models.md)** — [alphafold-3](entities/alphafold-3.md) still leads FoldBench at 64.9%; data, not scale, is the bottleneck.
- **[evo-2](entities/evo-2.md)** — 40B-parameter genomic FM; outperformed by 200M GPN-Star on variant effect prediction. "Scale alone isn't sufficient."
- These are upstream of clinical diagnostics but feed into diagnostic-test development and personalized medicine.

## Cross-cutting risk: failure modes and deployment hazards

- **[ai-hallucination-medical](concepts/ai-hallucination-medical.md)** — KaBLE belief-vs-fact (GPT-4o 98.2% → 64.4%); AA-Omniscience hallucination rates 22–94% across 26 models. Plus 2025 primary fragility findings: MetaMedQA (0% recall recognizing unanswerable questions), CRAFT-MD (GPT-4 0.82 → 0.63 vignette → conversation), NOTA (9–38% drop when correct answer replaced), SourceCheckup (50–90% of LLM responses partly unsupported by their own citations), illusion of multimodal readiness (Gu/Vozila Oct 2025).
- **[noharm](concepts/noharm.md)** — ARISE's safety benchmark: severe harm in **up to 22% of cases across 31 LLMs**, **77% errors of omission**. MedQA scores correlate only moderately (R = 0.61–0.64) with NOHARM safety. Three-agent advisor + guardian architectures show ~6× higher safety quartile odds.
- **[automation-bias-medical-ai](concepts/automation-bias-medical-ai.md)** — even AI-trained physicians show automation bias when fed planted erroneous LLM output (85% → 73% accuracy, Qazi medRxiv Sept 2025).
- **[ai-deskilling](concepts/ai-deskilling.md)** — first hard 2025 evidence (Budzyn Lancet GH Oct 2025): colonoscopy ADR fell 28.4% → 22.4% in same endoscopists 3 months after AI exposure (OR 0.69 adjusted).

## Frontier topics with thinner first-source coverage

- **[digital-twins-medicine](concepts/digital-twins-medicine.md)** — large publication/patent growth; only 12.1% of studies meet NASEM definition; Twin Health diabetes RCT (n=150) is the strongest result.
- Multimodal biomedical AI publications grew 2 (2021) → 462 (2025). Vision-language and vision-omics models are the leading subcategories.
- Patient perspectives literature grew 9 (2020) → 102 (2025); demographic disparities in acceptance documented; provider endorsement is the key determinant.

## Working hypothesis (refined 2026-05-10 post-ARISE)

> The 2026 state of the field is **two-track, with a third emerging**. (1) Narrow tools, clinician-in-loop, well-defined workflows — the strong-evidence track (ambient scribes, mammography AI, stroke imaging, sepsis prediction, ophthalmology copilots). (2) Open-ended LLM reasoning — strong benchmark numbers, dangerous failure modes (NOHARM, MetaMedQA, CRAFT-MD), thin prospective evidence. (3) **LLM-as-copilot in real care** — emerging, with the Penda Health Kenya deployment as the first large-N prospective example (39,849 visits, 16% diagnostic-error reduction). The deployed-LLM-copilot category may collapse the "narrow vs. open" split as it matures. Bridging the gap depends on: better benchmarks ([healthbench](concepts/healthbench.md), [medhelm](concepts/medhelm.md), [medagentbench](concepts/medagentbench.md), [noharm](concepts/noharm.md)); workflow design (the optimization paradox is a sober warning); regulatory iteration (PCCPs under the [fda-510k-pathway](concepts/fda-510k-pathway.md)); and clinician training to manage [automation-bias-medical-ai](concepts/automation-bias-medical-ai.md) and [ai-deskilling](concepts/ai-deskilling.md). Multi-agent **safety** (NOHARM advisor + guardian, ~6× safer) may be a more important deployment-relevant property than multi-agent **accuracy**.

## Sources awaiting ingest in `raw/`
- `raw/clinpract-15-00169.pdf` — Ogut MDPI *Clinics and Practice* Sept 2025, AI in clinical medicine review across 5 domains. On-topic, queued.
- `raw/claudes-constitution_webPDF_26-02.02a.pdf` — Anthropic, Claude's Constitution. Methodology/model-behavior document; relevance to medical diagnostics is indirect (deployment-safety, refusal behavior in clinical contexts) — TBD on ingest.

## Open questions to drive sourcing
- The **ARISE 10 predictions for 2026** are themselves usable — particularly (1) first malpractice lawsuit involving AI, (4) AI-bot arms race in prior auth/claims, (6) >people receive AI care than human care, (7) >90% of clinical-note text is AI-generated. Each is a candidate concept page if/when evidence emerges.
- **Bedi/Shah JAMA Jan 2025 (n=519 LLM evaluation studies)** — primary source for the "5%" statistic; ingest as primary.
- **NOHARM (Wu/Goh ArXiv Dec 2025)** primary paper.
- **TREWS / COMPOSER primary publications** — verify the prospective deployment effect sizes.
- Recent **NEJM AI** and **JAMA Network Open** issues for the prospective imaging trials (MASAI, NOTIFY-1, NOTIFY-EXTEND).
- **FDA 510(k) AI/ML device database** for current cleared-device list and labeling claims.
- Stanford Health Care's **FURM framework** documentation (governance counterpart).
- **State of clinical AI in non-US contexts** — most patient-perception studies originate in U.S./U.K./Germany; equity-focused literature is overwhelmingly skewed to high-income contexts. Penda Health Kenya is a notable counter-data-point.
