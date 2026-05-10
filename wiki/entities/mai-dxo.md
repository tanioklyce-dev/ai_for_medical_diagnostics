---
type: entity
title: Microsoft AI Diagnostic Orchestrator (MAI-DxO)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/mai-dxo-sequential-diagnosis-2025.md, ../sources/arise-state-of-clinical-ai-2026.md, ../sources/ai-index-2026.md]
tags: [model-family/llm, model-family/foundation-model, task/diagnosis, organization/microsoft, evaluation/external-validation]
---

# Microsoft AI Diagnostic Orchestrator (MAI-DxO)

A **model-agnostic multi-agent orchestrator** built on top of frontier LLMs for sequential clinical diagnosis. Microsoft AI's marquee 2025 diagnostic-AI result, now grounded in the primary publication [Sequential Diagnosis with Language Models](../sources/mai-dxo-sequential-diagnosis-2025.md) (Nori, Daswani, Kelly, Lundberg, Ribeiro, Wilson, Liu, Sounderajah, Carlson, Lungren, Gross, Hames, Suleyman, King, [Horvitz](eric-horvitz.md), ArXiv 2506.22405v2, Jul 2025). Co-developed with [sdbench](../concepts/sdbench.md), the benchmark it was designed to evaluate against.

## Headline results

Paired with OpenAI o3, evaluated on the 304-case [sdbench](../concepts/sdbench.md):

| Configuration | Accuracy | Cost / case |
|---|---|---|
| **MAI-DxO (ensemble)** | **85.5%** | $7,184 |
| **MAI-DxO (unconstrained)** | **81.9%** | $4,735 |
| MAI-DxO ($8k budget) | 80% | ~$5,000 |
| MAI-DxO ($4k budget) | ~75% | ~$2,500 |
| **MAI-DxO ($2k budget, cost-optimized)** | **79.9%** | **$2,397** |
| MAI-DxO (questions only) | ~50% | ~$300 |
| MAI-DxO (instant answer) | ~37% | $0 |
| Off-the-shelf o3 (baseline prompt) | 78.6% | $7,850 |
| **21 physicians (unaided generalists)** | **19.9%** | $2,963 |
| Highest-performing individual physician | 41% | — |

**MAI-DxO + o3 establishes Pareto dominance over both off-the-shelf models and physicians at every price point.** The cost-optimized configuration achieves comparable accuracy to off-the-shelf o3 at ~70% lower cost. The ensemble configuration achieves the headline 85.5% commonly cited in secondary summaries.

## Architecture — the five-agent virtual panel

A single base LLM role-plays five named virtual physicians that deliberate via a structured "Chain of Debate" before each action:

| Agent | Role |
|---|---|
| **Dr. Hypothesis** | Maintains probability-ranked top-3 differential; Bayesian update after each new finding. |
| **Dr. Test-Chooser** | Selects ≤3 diagnostic tests per round that maximally discriminate between leading hypotheses. |
| **Dr. Challenger** | Devil's advocate. Flags anchoring bias, surfaces contradictory evidence, proposes tests that could falsify the leading diagnosis. |
| **Dr. Stewardship** | Cost-conscious. Advocates cheaper alternatives when diagnostically equivalent; vetoes low-yield expensive tests. |
| **Dr. Checklist** | Silent quality control on test naming and internal consistency. |

After Chain of Debate, the panel commits to one of three actions: **ask question**, **request test**, or **provide diagnosis**. An optional **budget tracker** (separately orchestrated LM call) estimates cumulative cost before tests are ordered.

This architecture is the 2025 LLM realization of a research agenda [eric-horvitz](eric-horvitz.md) has been pursuing since the **Pathfinder** Bayesian pathology system (Heckerman, Horvitz, Nathwani 1992). The MAI-DxO paper's Section 5.2 explicitly traces the lineage. Dr. Hypothesis ≈ Bayesian belief network over diseases; Dr. Test-Chooser ≈ value-of-information–maximizing test selector. The novelty is **realizing these normative principles via LLM role-play instead of hand-engineered Bayesian network**.

## Five configuration variants

| Variant | Description |
|---|---|
| Instant Answer | Diagnose from vignette alone, no questions/tests |
| Question Only | Can ask questions but cannot order tests |
| Budgeted | Cumulative cost tracker enforces a max budget; can cancel tests after price reveal |
| Unconstrained Budget | Full panel, no cost tracking |
| Ensemble | Multiple parallel panels + a final aggregation panel that picks best diagnosis |

The variants span the cost-accuracy Pareto frontier. The paper recommends configuring to the institution's cost tolerance.

## Model-agnostic boost (across 10 frontier LLMs)

MAI-DxO was primarily developed using GPT-4.1, but the orchestration generalizes:

| Base model | Baseline accuracy | + MAI-DxO | Δ |
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

**Average gain: +11 percentage points.** All gains *p* < 0.005 (paired permutation test). Gains are *largest for weaker baselines*, suggesting MAI-DxO compensates for model weakness via structured-reasoning scaffolding. Cost reductions for o3 and o4-mini are very significant even where raw accuracy gain is modest.

## Validity and held-out test set

- **Cohen's κ for Judge–physician agreement on diagnoses**: 0.70 (MAI-Dx set) vs 0.87 (human-vs-human on same diagnoses).
- In 4 of 5 disagreement cases, physicians judged the Judge **overly strict** — implying reported accuracy may slightly *underestimate* true performance.
- The 56 most recent CPC cases (2024–2025, published after model training cutoffs) were held out as a hidden test set. **Relative gains preserved on the held-out test set** — robust against memorization.
- See [sdbench](../concepts/sdbench.md) for full benchmark methodology.

## Stated limitations (explicit in source, Section 5.3)

1. **NEJM CPC cases are pedagogically curated** for difficulty. Common, benign presentations aren't represented. **The benchmark cannot measure false positives** — exactly the safety axis [noharm](../concepts/noharm.md) targets.
2. **Physician comparison is constrained, not realistic.** Participants were explicitly forbidden from external resources (no search, no LLMs, no EHRs, no colleagues) to prevent them from looking up online NEJM cases. The paper acknowledges this is "not reflective of real clinical practice."
3. **Generalists only** (17 PCPs + 4 in-hospital generalists). NEJM CPCs would typically warrant specialist referral; specialists would likely outperform.
4. **Cost estimates are first-order**: U.S. CPT pricing, excludes invasiveness, time-to-result, wait times, geographic/payer variation, authorization.
5. **No real-world deployment evidence yet** — the paper explicitly states *"these results do not yet establish the clinical efficacy of MAI-DxO in real-world decision support."*

## The qualitative-mechanism example

Section 4 gives a representative case: a patient hospitalized for alcohol withdrawal **ingested hand sanitizer** in the hospital → intoxication. Off-the-shelf o3 fixated on antibiotic toxicity, ordered brain MRI + EEG ($3,431), and produced the wrong diagnosis. MAI-DxO's Dr. Hypothesis flagged in-hospital toxin exposures in round 1; the panel asked about hand-sanitizer ingestion before ordering tests, eliciting the patient's confession, and reached the correct diagnosis via a $795 toxic-alcohol panel.

The architectural payoff: **explicit hypothesis tracking + adversarial challenge + cost stewardship** produces a different reasoning path, not just a more confident one.

## Open questions

- **Real-world deployment.** Not yet tested in prospective patient care. The paper flags this as the next milestone.
- **FDA pathway.** Whether Microsoft is pursuing [fda-510k-pathway](../concepts/fda-510k-pathway.md) authorization for any specific clinical use case is not stated.
- **Performance on [noharm](../concepts/noharm.md).** Severe-harm probability in real specialist consults is the safety axis that sequential-diagnosis-accuracy doesn't measure. Multi-agent advisor + guardian systems show ~6× higher safety odds on NOHARM — MAI-DxO's specific architecture has not been tested.
- **Equity.** Demographic distribution of NEJM CPC cases is itself a selection bias; performance on under-represented populations is open.
- **Specialist comparison.** The paper notes specialist physicians would likely perform better on CPCs than the recruited generalists. A specialist baseline is the missing comparator.
- **Optimization-paradox robustness.** Bedi/Shah ArXiv Jun 2025 (referenced in this paper as Bedi 2025b) shows naive multi-agent ensembles can underperform less-engineered ones. MAI-DxO's specific design appears robust, but the generalization to other architectures is not.

## Related
- [sdbench](../concepts/sdbench.md) — the benchmark methodology MAI-DxO was evaluated against.
- [eric-horvitz](eric-horvitz.md) — the foundational-Bayesian-decision-theory lineage MAI-DxO descends from.
- [agentic-clinical-ai](../concepts/agentic-clinical-ai.md) — the broader category. Includes the optimization-paradox caveat.
- [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md) — single-LLM baseline context (o1-preview / Brodeur).
- [amie](amie.md) — Google's diagnostic-dialogue counterpart with overlapping evidence base (Multi-visit, multimodal, OSCE-style dialogue).
- [clinical-validation](../concepts/clinical-validation.md) — case-bench-vs-real-practice context.

## Sources
- [mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md) — **primary citation** (this is the authoritative source for all MAI-DxO claims).
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (slide 45, secondary summary).
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2, p. 272–273, summary).
