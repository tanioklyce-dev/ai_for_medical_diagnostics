---
type: source
title: Sequential Diagnosis with Language Models (Microsoft AI / MAI-DxO)
authors: [Harsha Nori, Mayank Daswani, Christopher Kelly, Scott Lundberg, Marco Tulio Ribeiro, Marc Wilson, Xiaoxuan Liu, Viknesh Sounderajah, Jonathan M Carlson, Matthew P Lungren, Bay Gross, Peter Hames, Mustafa Suleyman, Dominic King, Eric Horvitz]
published: 2025-07-03
ingested: 2026-05-10
source_path: raw/mai_dxo_sequential_diagnosis_2025.pdf
url: https://arxiv.org/abs/2506.22405
arxiv_id: 2506.22405v2
pages: 31
license: arXiv non-exclusive (preprint)
tags: [model-family/llm, model-family/foundation-model, task/diagnosis, organization/microsoft, evaluation/benchmark, evaluation/external-validation]
---

# Sequential Diagnosis with Language Models

> Microsoft AI's primary publication for the **MAI Diagnostic Orchestrator (MAI-DxO)** and the **Sequential Diagnosis Benchmark (SDBench)**, released as ArXiv 2506.22405 on July 3, 2025. Author list includes Harsha Nori (lead) and Eric Horvitz (Microsoft Chief Scientific Officer; coauthor of much of the foundational diagnostic-decision-support literature dating back to Pathfinder in 1992 — see [eric-horvitz](../entities/eric-horvitz.md)). Authoritative version of the work that ARISE 2026 and the AI Index 2026 cite secondhand.

## Summary

Two artifacts:

1. **SDBench (Sequential Diagnosis Benchmark)** — a benchmark methodology that recasts 304 New England Journal of Medicine clinicopathological-conference (CPC) cases (2017–2025) as **stepwise diagnostic encounters** rather than static vignettes. A diagnostic agent (human or AI) starts with a 2–3 sentence case abstract and must iteratively choose to **ask questions**, **request tests**, or **commit to a final diagnosis**, with each test costing money. See [sdbench](../concepts/sdbench.md).

2. **MAI-DxO (MAI Diagnostic Orchestrator)** — a model-agnostic orchestrator that wraps a base LLM in a panel of five named virtual physicians ("Dr. Hypothesis," "Dr. Test-Chooser," "Dr. Challenger," "Dr. Stewardship," "Dr. Checklist") that deliberate via a **Chain of Debate** before each action. See [mai-dxo](../entities/mai-dxo.md).

The headline result confirms both summaries the wiki had previously ingested via [arise-state-of-clinical-ai-2026](arise-state-of-clinical-ai-2026.md) and [ai-index-2026](ai-index-2026.md): paired with OpenAI's o3, MAI-DxO achieves **80% diagnostic accuracy** at $4,735 (the unconstrained-budget configuration) — four times the 19.9% accuracy of 21 generalist US/UK physicians at $2,963 average cost. The cost-optimized configuration achieves 79.9% at $2,397 (≈70% lower than off-the-shelf o3 at $7,850). The ensemble configuration hits **85.5% at $7,184**. MAI-DxO's gains generalize across 10 frontier models from Anthropic, Google, OpenAI, xAI, Meta, and DeepSeek — **average +11 percentage points** of accuracy.

The paper's deeper contribution is methodological. SDBench introduces three innovations that make case-bench-style evaluation closer to clinical reality: (1) a **Gatekeeper agent** (o4-mini) that holds the full case file and reveals findings only when explicitly queried, refusing diagnostic interpretations and only disclosing pathognomonic results when the exact confirmatory test is requested; (2) **synthetic findings** for queries not in the original case (numerically/descriptively consistent with the rest of the case) so models can pursue alternative diagnostic paths without leaking information; (3) a **Judge agent** (o3 with a 5-point physician-authored Likert rubric) validated against in-house physician adjudication at Cohen's κ = 0.70 (vs human-vs-human κ = 0.87) — physicians judged the automated Judge "overly strict" in 4 of 5 disagreement cases, suggesting reported MAI-DxO accuracy may modestly underestimate true performance.

## Key claims and findings

### Headline numbers (Section 4 / Figure 7)

| System | Accuracy | Cost / case |
|---|---|---|
| **MAI-DxO (ensemble) + o3** | **85.5%** | $7,184 |
| **MAI-DxO (unconstrained) + o3** | **81.9%** | $4,735 |
| **MAI-DxO ($8k budget) + o3** | **80%** | ~$5,000 |
| MAI-DxO ($4k budget) + o3 | ~75% | ~$2,500 |
| MAI-DxO ($2k budget) + o3 | **79.9%** (cost-optimized config) | $2,397 |
| MAI-DxO (questions only) + o3 | ~50% | ~$300 |
| MAI-DxO (instant answer) + o3 | ~37% | $0 |
| Off-the-shelf o3 (baseline prompt) | 78.6% | $7,850 |
| Off-the-shelf GPT-4o | 49.3% | $2,745 |
| **21 physicians (unaided)** | **19.9%** | $2,963 |
| Highest-performing individual physician | 41% | — |

**MAI-DxO + o3 establishes Pareto dominance over both off-the-shelf models and physicians at every cost level.** *Quote, Section 4: "Even the physician performing at the highest diagnostic accuracy (41%) was outperformed by GPT-4o in both accuracy and cost."*

### Five-agent architecture (Section 3.2)

- **Dr. Hypothesis** — maintains probability-ranked top-3 differential, Bayesian updates after each finding.
- **Dr. Test-Chooser** — selects up to 3 diagnostic tests per round that maximally discriminate between leading hypotheses.
- **Dr. Challenger** — devil's advocate: identifies anchoring bias, flags contradictory evidence, proposes falsifying tests.
- **Dr. Stewardship** — enforces cost-conscious care; advocates cheaper alternatives, vetoes low-yield expensive tests.
- **Dr. Checklist** — silent quality control on test naming and panel-internal consistency.

After a **Chain of Debate** between agents, the panel commits to one of three actions: ask question, request test, or diagnose. An optional **budget tracker** is invoked before tests to estimate cumulative cost.

### Five MAI-DxO variants

| Variant | Description |
|---|---|
| Instant Answer | Diagnosis from initial vignette only; no follow-up |
| Question Only | Panel can ask questions but cannot order tests |
| Budgeted | Cumulative cost tracker + max budget; can cancel tests after price reveal |
| Unconstrained Budget | Full panel, no cost tracking |
| Ensemble | Multiple parallel panels + final aggregation panel |

MAI-DxO was primarily developed and optimized using GPT-4.1 but is **explicitly model-agnostic**.

### Model-agnostic boost (Figure 8, 10 models tested)

Average +11 percentage-point accuracy gain across all sufficiently capable foundation models:

| Base model | Baseline | + MAI-DxO | Δ |
|---|---|---|---|
| Claude 4 Sonnet | 63.2% | 72.4% | +9.2 |
| Claude 4 Opus | 68.4% | 83.2% | +14.8 |
| Gemini 2.5 Flash | 56.2% | 68.4% | +12.2 |
| Gemini 2.5 Pro | 68.8% | 78.6% | +9.8 |
| GPT-4.1 | 61.8% | 72.0% | +10.2 |
| o4-mini | 69.4% | 72.0% | +2.6 |
| o3 | 78.6% | 81.9% | +3.3 |
| Grok-3 | 59.9% | 75.7% | +15.8 |
| Llama 4 Maverick | 53.6% | 69.1% | +15.5 |
| DeepSeek-R1 | 47.4% | 65.5% | +18.1 |

All gains statistically significant at *p* < 0.005 (one-sided paired permutation test, 10,000 resamples). Gains are *largest for weaker baselines*, suggesting MAI-DxO compensates for model weakness via structured-reasoning scaffolding rather than simply amplifying strong models. Cost reductions for o3 and o4-mini are very significant even where raw accuracy gain is small.

### Train/test split (robustness check)

The 56 most recent CPC cases (2024–2025) were held out as a **hidden test set**, not seen during dev. MAI-DxO's relative gains over off-the-shelf models are preserved on the test set (see Figure 9 in source). This is a meaningful methodological concession — many clinical-AI papers use full-case-pool evaluation, leaving room for inadvertent overfitting.

### Validity of the Judge

- Cohen's κ = **0.70** for MAI-Dx vs in-house-physician scoring.
- Cohen's κ = **0.87** for human-vs-human scoring on the same diagnoses.
- In 4 of 5 disagreement cases, in-house physicians judged the automated Judge to be **overly strict** (marking correct diagnoses as incorrect) — implying the reported MAI-DxO accuracy may slightly **underestimate** true performance.

### Cost methodology

- Each physician visit fixed at $300; multiple sequential questions count as one visit, terminated by a test request.
- Diagnostic tests priced via LLM-based CPT-code lookup against a 2023 pricing table from a large U.S. health system (CMS HHS price-transparency rule, 45 CFR §180). 98% of test requests successfully matched a CPT code.
- *Caveat from the paper*: cost estimates are **first-order approximations**; geographic, payer, and provider variation is not modeled. Costs beyond the test itself (physician reporting time, device maintenance, patient travel, wait times) are excluded. Cost is consistent across all agents, so relative comparisons are meaningful even if absolute numbers are first-order.

### Physician comparison setup (Section 3.3)

- **21 generalist physicians** (US or UK), median 12 years experience [IQR 6–24]. 17 PCPs, 4 in-hospital generalists.
- Each completed an average of 36 cases for **764 total diagnoses** on the 56-case test set.
- 11.8 minutes average per case. Average **6.6 questions, 7.2 tests** per case.
- **Explicitly forbidden** from external resources: no search engines, no LLMs (ChatGPT, Gemini, Copilot), no online medical references. Justification: NEJM cases are publicly accessible online; restricting search prevents physicians from looking up the answer. The paper acknowledges in Section 5.3 that this is *"not reflective of real clinical practice"* — physicians normally have EHRs, colleagues, textbooks, and increasingly LLMs available.
- Physicians blinded to the correctness of their diagnosis during the study; case order randomized.

### Stated limitations (Section 5.3)

The paper explicitly flags:

1. **Case-distribution skew**: NEJM CPC cases are pedagogically curated for difficulty. Real-world deployments include common, benign, healthy presentations — *the paper does not measure false-positive rates*.
2. **Physician comparison is conservative-not-realistic**: real practice has external resources, EHRs, specialists, longitudinal context.
3. **Generalists only**: NEJM CPCs often warrant specialist referral. Specialists would likely outperform the recruited generalists on subspecialty cases.
4. **Cost estimates are first-order**.
5. **Scope of "value beyond diagnosis"**: invasiveness, patient discomfort, wait times, authorization/reimbursement constraints not modeled.

### Implications and future work (Section 5.4)

- "*While these results do not yet establish the clinical efficacy of MAI-DxO in real-world decision support, they underscore AI's increasing potential to address urgent challenges in healthcare delivery.*"
- Model-agnostic design avoids "version chasing" — health systems can adopt MAI-DxO and swap base LLMs as they evolve.
- Hypothesized highest impact in **resource-limited settings** with workforce shortages; potential for direct-to-consumer smartphone-based triage if safety, regulatory, and privacy guardrails are in place.
- Future work: evaluate in real clinical environments where prevalence and case-mix differ from NEJM CPCs.
- Mentions multimodal extension (imaging) as a likely accuracy-and-efficiency lever.

## Entities and concepts touched

**Updated existing pages:** [mai-dxo](../entities/mai-dxo.md) (now grounded in primary source — full architectural detail), [agentic-clinical-ai](../concepts/agentic-clinical-ai.md), [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md), [clinical-validation](../concepts/clinical-validation.md), [arise-state-of-clinical-ai-2026](arise-state-of-clinical-ai-2026.md) (cross-link).

**New pages from this ingest:**
- [sdbench](../concepts/sdbench.md) — the benchmark methodology, separable from the orchestrator.
- [eric-horvitz](../entities/eric-horvitz.md) — connects MAI-DxO, ARISE, AMIE-adjacent work, and decades of foundational diagnostic-decision-support theory back to Pathfinder (1992).

## Notes

- **Citation precedence**: this is now the primary source for MAI-DxO claims. Both [arise-state-of-clinical-ai-2026](arise-state-of-clinical-ai-2026.md) and [ai-index-2026](ai-index-2026.md) summarize this paper; they should be treated as secondary on MAI-DxO specifics.
- **Benchmark release status**: as of paper submission, "we are in the process of submitting this work for external peer review and are actively working with partners to explore the potential to release SDBench as a public benchmark." Watch for the public release — if it lands, SDBench may become a load-bearing benchmark for sequential-diagnosis evaluation.
- **Conflict-of-interest context**: this is a Microsoft AI paper, evaluating Microsoft's orchestrator on a benchmark of Microsoft's design, with most authors at Microsoft. The Cohen's κ judge-validation step is the strongest mitigating evidence; the held-out test set is another.
- **The "instructive case" example (Section 4, hand-sanitizer alcohol-withdrawal)**: off-the-shelf o3 fixated on antibiotic toxicity and ordered brain MRI + EEG ($3,431) → wrong diagnosis. MAI-DxO's Dr. Hypothesis flagged the need to consider in-hospital toxin exposures in round 1; the panel asked about hand-sanitizer ingestion, eliciting a confession, leading to a targeted toxic-alcohol panel and correct diagnosis at $795. *This is the qualitative mechanism the architecture buys you* — explicit hypothesis-tracking and adversarial challenge.
- **Cross-reference with the optimization paradox** ([agentic-clinical-ai](../concepts/agentic-clinical-ai.md)): Bedi/Shah ArXiv Jun 2025 (referenced in this paper as Bedi 2025b) shows naive ensembles can underperform less-engineered ones. MAI-DxO's careful role design and information-flow choreography appears to be exactly what the optimization paradox warns is necessary.
- **Companion to the broader 2025 case-bench cohort**: the Brodeur et al. 2024 paper (referenced here, primary o1-preview NEJM-CPC paper at 78% Dx / 87% next-test selection) is the closest single-LLM benchmark; AMIE (Tu Nature 2025) is the closest multi-agent dialogue counterpart. MAI-DxO is the marquee example of multi-agent + sequential-decision + cost-aware design.
- **Adjacent sources to ingest next**: Brodeur et al. ArXiv 2024 (`arxiv.org/abs/2412.10849`) — would close the loop on the o1-preview / NEJM CPC primary citation that [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md) currently has secondhand; Bedi/Shah JAMA Jan 2025 — the "5%" stat primary; NOHARM (Wu/Goh ArXiv Dec 2025).
