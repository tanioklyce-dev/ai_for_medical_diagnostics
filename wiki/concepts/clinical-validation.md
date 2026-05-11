---
type: concept
title: Clinical validation of medical AI
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md, ../sources/mai-dxo-sequential-diagnosis-2025.md, ../sources/ogut-ai-clinical-medicine-2025.md, ../sources/do-olmo-dxgpt-rare-disease-2024.md]
tags: [evaluation, governance, prospective-trial, evidence]
---

# Clinical validation of medical AI

The central evidence tension in 2025 medical AI: deployment is accelerating much faster than the rigorous evidence base. Most published clinical AI evaluations are not done on real patients — they are done on **exam-style questions, retrospective benchmarks, or curated case series**.

## The headline finding (2026) — primary citation

The "5% used real clinical data" critique now has a **primary citation**: **Bedi, Shah et al., JAMA Jan 2025** — a systematic review of **n=519 LLM-evaluation studies (2022–2024)**. Key findings:

- **95%** of studies used **accuracy** as the primary evaluation metric.
- **Only 5%** used real patient data; the rest used exam-style questions, vignettes, or synthetic data.
- Most-evaluated tasks: medical-licensing-exam questions (45%) and clinical diagnoses (19%).
- Almost-never-evaluated tasks: assigning billing codes (0.2%), writing prescriptions (0.2%) — i.e., the administrative tasks clinicians most want help with (see [medhelm](medhelm.md)).
- Fairness, bias, and toxicity studied in 16% of papers; deployment considerations in 5%; calibration / uncertainty in 1%.

This finding is summarized via [arise-network](../entities/arise-network.md)'s inaugural [State of Clinical AI Report 2026](../sources/arise-state-of-clinical-ai-2026.md), which is the primary lens for this wiki on the evidence-base critique. ARISE's overall conclusion: AI performs most effectively when **supporting rather than replacing** clinician judgment.

A separate peer-reviewed analysis ([Singh et al., 2025](https://www.bmj.com/)) of 1,016 FDA AI/ML device authorizations through Dec 2024 found that **only 2.4%** of devices with clinical studies were supported by randomized controlled trial data, with nearly all entering via the [fda-510k-pathway](fda-510k-pathway.md).

## What "validation" can mean (gradient of rigor)

| Level | What it tests | How common in 2025 |
|---|---|---|
| Exam-style Q&A (e.g., USMLE) | Knowledge recall on standardized prompts | ~half of 500+ studies (ARISE) |
| Retrospective benchmark on curated images | Ability to match reference labels on past data | Dominant in imaging AI publications |
| Reader study with clinicians | Clinician-AI pair vs. clinician-alone, retrospective | Used for many FDA submissions |
| Prospective clinical trial | AI evaluated on live patient data with predefined endpoints | 536 imaging-AI papers in 2025 (up 28.5% YoY from 417) |
| RCT with patient outcomes | Direct comparison with randomization | Rare; only 2.4% of devices |

## The narrow-tool vs. open-LLM distinction

Evidence-base concerns apply most sharply to **general-purpose LLMs in open-ended clinical reasoning**:

- [noharm](noharm.md) (Wu/Goh ArXiv Dec 2025): up to **22% of consult cases** show severely harmful LLM recommendations across 31 LLMs; **77% are errors of omission**. Standard knowledge benchmarks correlate only moderately (R=0.61–0.64) with NOHARM safety scores.
- **MetaMedQA** (Griot Yuskel Nature Communications Jan 2025): 12 LLMs all show 0% recall at recognizing unanswerable / malformed questions — a metacognitive failure mode.
- **CRAFT-MD** (Johri Rajpurkar Nature Medicine Jan 2025): GPT-4 accuracy collapses 0.82 → 0.63 going from static vignette to multi-turn dialogue. Robustness fragility.
- "**None of the other answers**" failure mode (Bedi/Shah JAMA Network Open Aug 2025): replacing the correct answer with NOTA drops frontier-model MedQA accuracy 9–38% — strong MCQ performance is partly pattern-matching, not reasoning.

By contrast, **narrow tools operating in constrained workflows with clinician oversight have generated much stronger real-world evidence**:
- [ambient-ai-scribes](ambient-ai-scribes.md) — multiple multi-site outcomes papers and the first two RCTs (modest objective time savings, real burnout reduction).
- [ai-consult-penda](../entities/ai-consult-penda.md) — first prospective LLM-copilot deployment in real care (Penda Health Kenya, 39,849 visits, 16% diagnostic-error reduction). Note: *this is an LLM not a narrow tool*, suggesting the "narrow vs. open" line is starting to blur.
- [dxgpt](../entities/dxgpt.md) ([foundation29](../entities/foundation29.md)) — free web tool + Madrid public-system integration (~6,000 doctors), 500k+ global users for rare-disease decision support. Parallel deployed-LLM-copilot exemplar to Penda, with a different shape (public/web/nonprofit vs. single-vendor RCT). **No published outcomes evidence yet** — operational counts only — but the team has prospective studies in progress ([do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md) §5.1).
- AI sepsis prediction — [trews](../entities/trews.md) and COMPOSER reported absolute mortality reductions in prospective deployments.
- AI-assisted mammography — Vara MG (Eisemann Nature Medicine Jan 2025), 12 sites, 463k women, 17.6% increase in cancer detection, recall slightly *lower*.
- Brainomix 360 stroke (Nagaratnam Lancet Dec 2025) — 26 NHS hospitals, EVT rates doubled (2.3%→4.6%) at AI sites.

This distinction shows up repeatedly in governance frameworks (FURM, GUIDE-AI Lab) and remains the load-bearing organizing principle for the wiki — but the LLM-copilot deployments are an emerging third category.

## Notable 2025 prospective clinical trials cited

- **MASAI** — randomized study of AI-assisted mammography reading (screening accuracy).
- **NOTIFY-1, NOTIFY-EXTEND** — tested whether flagging early signs of heart disease that AI spotted on routine CT scans changed clinician behavior (preventive cholesterol prescription).

The growth from 417 (2024) → 536 (2025) prospective imaging trial papers is a good proxy for the maturation of the field — but baseline volume is still small relative to the >5,000 medical AI papers published in 2025.

## Governance frameworks

- **Stanford Health Care's FURM framework** — governs all new AI tool adoptions at the institution.
- **GUIDE-AI Lab** — working to make FURM available to other health systems.
- See also general RAI standards being adopted in healthcare: NIST AI RMF, ISO/IEC 42001, EU AI Act high-risk obligations.

## Open questions

- How do "real clinical data" requirements get operationalized for foundation-model-based diagnostics, where pretraining data is sprawling and unverifiable?
- What's the FDA's evolving stance on Predetermined Change Control Plans (PCCPs) — used in ~10% of 2025 clearances — and how do they interact with post-market validation?
- Where are the dark spots — specialties with high adoption but minimal prospective evidence (e.g., parts of radiology, pathology)?
- What's the calibration story? AI may achieve high AUC but be poorly calibrated, leading to over/under-treatment downstream.

## Pre-2025 ML-CDSS evidence-base finding (Vasey 2021)

A pre-existing primary citation that complements the Bedi/Shah JAMA Jan 2025 "5%" finding: **Vasey, Ursprung, Beddoe et al., *JAMA Network Open* 2021** — systematic review of **37 ML-based clinical decision support studies**:

- **~half showed improvement in clinician diagnostic performance.**
- **~half showed no change or inconclusive results.**
- **No clear improvement was observed in studies simulating real-world clinical settings.**

Vasey 2021 sits in the literature as the pre-2025 anchor for the CDSS-evidence-base gap; Bedi/Shah JAMA Jan 2025 is the 2025 update at much larger n (519 vs 37). Together they make a strong case that *the published improvement claims for ML-CDSS have been historically softer than headlines suggest*, with the real-world-setting subset being the weakest. Surfaced via [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md), Section 3.2.

## Reporting-guideline standards (CONSORT-AI / SPIRIT-AI)

Two extensions of the CONSORT and SPIRIT clinical-trial reporting standards specifically for AI interventions: **CONSORT-AI** (reporting completed trials) and **SPIRIT-AI** (protocol design for trials of AI interventions), both Ibrahim, Liu, Rivera et al. *Trials* 2021 / *Nature Medicine* 2020 / *Lancet Digital Health* 2020. These are the appropriate quality bar for prospective AI trials; adoption is the right metric for evidence-base maturity. ARISE 2026's 10-prediction list does *not* expect significant FDA regulatory progress in 2026, but standards-development at the journal / reviewer level may move faster.

## Sequential-diagnosis as a middle layer between vignette and trial

The MAI-DxO paper ([mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md)) introduces [sdbench](sdbench.md), a benchmark methodology that occupies a useful middle ground in the validation hierarchy: more realistic than static MCQ vignettes, less realistic than prospective deployment trials. Its three methodological contributions are worth knowing as the **emerging standard for case-bench-style evaluation in 2025–26**:

- **Gatekeeper agent** — holds the full case file but reveals findings only when explicitly queried, refusing diagnostic interpretations and disclosing pathognomonic results only when the exact confirmatory test is requested.
- **Synthetic findings** — for queries not in the original published case, the Gatekeeper returns numerically/descriptively consistent synthetic results so models can pursue alternative diagnostic paths without leakage hints. Physician panel validated: of 508 responses reviewed, only 8 flagged, 0 leaked the diagnosis.
- **LLM Judge with physician-authored rubric** — 5-point Likert (≥4 = correct), Cohen's κ = 0.70 vs physician adjudication (vs human-vs-human κ = 0.87).

These design patterns are likely to propagate; expect future clinical-AI benchmarks to follow similar templates.

**Important methodological note from the paper itself**: when physicians are recruited as the human comparator on case-bench evaluations of publicly-available cases (like NEJM), they are typically **forbidden from external resources** (search engines, LLMs, EHR access, colleagues) to prevent them from looking up the answer. The MAI-DxO paper acknowledges in Section 5.3 that this is *"not reflective of real clinical practice."* The implication for any "AI beats physicians 4×" headline: the human floor is artificial, not deployment-realistic. *This is the right way to do the case-bench experiment, but the result needs to be read accordingly.*

## Synthetic-vs-real-world performance gap (DxGPT preprint)

A clean in-paper demonstration of how much synthetic benchmarks overstate deployment-grade performance: [do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md) evaluates 13 LLMs on rare-disease diagnosis across one synthetic and two real-world datasets. Across **all 13 models**, top-1 (P1) accuracy drops **10–30 percentage points** going from GPT-4-generated synthetic cases to HPO-list real-world cases (RAMEDIS, PUMCH from RareBench):

| Model | Synthetic P1 | RAMEDIS P1 | PUMCH P1 |
|---|---|---|---|
| Claude 3 Opus | 72.5% | **55.0%** | 52.1% |
| GPT-4 Turbo 1106 | 68.5% | 51.5% | **59.5%** |
| Gemini 1.5 Pro | 70.0% | 42.6% | 47.3% |
| Llama 3 70B (open) | 64.0% | 53.5% | 44.4% |
| Llama 2 7B (open) | 30.5% | 25.6% | 18.9% |

The point isn't model ranking — it's that **the synthetic-benchmark numbers are systematically optimistic**. This pattern likely generalizes: any GPT-4-generated synthetic dataset risks both stylistic and content circularity with the GPT-4-family models being evaluated.

### LLM-as-judge circularity (a new methodological caveat to track)

The same DxGPT preprint uses **GPT-4 to generate synthetic cases AND as the LLM judge** scoring all 13 models' outputs. The authors acknowledge this in §4.4.2 (citing Shankar et al. 2024 ArXiv 2404.12272, *"Who Validates the Validators?"*): the method "while efficient, might overestimate the models' performance suggesting a need for validation through human expert evaluation in future studies." 

This is a distinct concern from [mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md)'s judge-vs-physician κ analysis (κ = 0.70, with physicians often judging the LLM judge *overly strict*). The two findings combined suggest LLM-as-judge can run in either direction depending on prompt design and whether the same model family generates the cases. Per-paper, ask: is the case generator the same family as the model under test, and is the judge family aligned with either? Trust single-judge benchmarks accordingly.

## Cross-cutting deployment concerns

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) adds two failure modes for clinician–AI teaming that complicate "validation" itself:

- [automation-bias-medical-ai](automation-bias-medical-ai.md) — Qazi et al. medRxiv Sept 2025: AI-trained physicians dropped from 85% → 73% accuracy when fed deliberately erroneous LLM output, despite voluntary AI consultation and prior AI-literacy training.
- [ai-deskilling](ai-deskilling.md) — Budzyn et al. Lancet GH Oct 2025: colonoscopy adenoma detection rate fell 28.4% → 22.4% in the same endoscopists 3 months *after* AI exposure.

Implication: a successful prospective trial of AI-assisted care does not by itself demonstrate that the *system* (clinicians + AI) will perform well at scale or over time.

## Sources
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (slides 5, 32, 70–72, throughout)
- [mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md) (Sections 2, 3.3, 5.3 — SDBench methodology and constrained-physician note)
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6, p. 271, 273, 278, including ARISE box)
- [ogut-ai-clinical-medicine-2025](../sources/ogut-ai-clinical-medicine-2025.md) (citation map for Vasey 2021 ML-CDSS systematic review and CONSORT-AI / SPIRIT-AI standards)
- [do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md) (synthetic-vs-real-world P1 gap across 13 LLMs on rare-disease diagnosis; LLM-as-judge circularity caveat)
