---
type: concept
title: Clinical validation of medical AI
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md, ../sources/mai-dxo-sequential-diagnosis-2025.md]
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

## Sequential-diagnosis as a middle layer between vignette and trial

The MAI-DxO paper ([mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md)) introduces [sdbench](sdbench.md), a benchmark methodology that occupies a useful middle ground in the validation hierarchy: more realistic than static MCQ vignettes, less realistic than prospective deployment trials. Its three methodological contributions are worth knowing as the **emerging standard for case-bench-style evaluation in 2025–26**:

- **Gatekeeper agent** — holds the full case file but reveals findings only when explicitly queried, refusing diagnostic interpretations and disclosing pathognomonic results only when the exact confirmatory test is requested.
- **Synthetic findings** — for queries not in the original published case, the Gatekeeper returns numerically/descriptively consistent synthetic results so models can pursue alternative diagnostic paths without leakage hints. Physician panel validated: of 508 responses reviewed, only 8 flagged, 0 leaked the diagnosis.
- **LLM Judge with physician-authored rubric** — 5-point Likert (≥4 = correct), Cohen's κ = 0.70 vs physician adjudication (vs human-vs-human κ = 0.87).

These design patterns are likely to propagate; expect future clinical-AI benchmarks to follow similar templates.

**Important methodological note from the paper itself**: when physicians are recruited as the human comparator on case-bench evaluations of publicly-available cases (like NEJM), they are typically **forbidden from external resources** (search engines, LLMs, EHR access, colleagues) to prevent them from looking up the answer. The MAI-DxO paper acknowledges in Section 5.3 that this is *"not reflective of real clinical practice."* The implication for any "AI beats physicians 4×" headline: the human floor is artificial, not deployment-realistic. *This is the right way to do the case-bench experiment, but the result needs to be read accordingly.*

## Cross-cutting deployment concerns

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) adds two failure modes for clinician–AI teaming that complicate "validation" itself:

- [automation-bias-medical-ai](automation-bias-medical-ai.md) — Qazi et al. medRxiv Sept 2025: AI-trained physicians dropped from 85% → 73% accuracy when fed deliberately erroneous LLM output, despite voluntary AI consultation and prior AI-literacy training.
- [ai-deskilling](ai-deskilling.md) — Budzyn et al. Lancet GH Oct 2025: colonoscopy adenoma detection rate fell 28.4% → 22.4% in the same endoscopists 3 months *after* AI exposure.

Implication: a successful prospective trial of AI-assisted care does not by itself demonstrate that the *system* (clinicians + AI) will perform well at scale or over time.

## Sources
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (slides 5, 32, 70–72, throughout)
- [mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md) (Sections 2, 3.3, 5.3 — SDBench methodology and constrained-physician note)
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6, p. 271, 273, 278, including ARISE box)
