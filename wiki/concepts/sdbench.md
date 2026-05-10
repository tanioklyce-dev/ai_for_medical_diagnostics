---
type: concept
title: SDBench — Sequential Diagnosis Benchmark
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/mai-dxo-sequential-diagnosis-2025.md]
tags: [evaluation/external-validation, task/diagnosis, model-family/llm, evaluation/benchmark]
---

# SDBench (Sequential Diagnosis Benchmark)

A 2025 benchmark methodology from Microsoft AI ([Nori, Horvitz et al., ArXiv 2506.22405](../sources/mai-dxo-sequential-diagnosis-2025.md)) that recasts **304 New England Journal of Medicine clinicopathological-conference (CPC) cases (2017–2025)** as interactive **stepwise diagnostic encounters** instead of static multiple-choice vignettes. Built as a substrate for evaluating [mai-dxo](../entities/mai-dxo.md), but designed as a generalizable benchmark applicable to any diagnostic agent (LLM or human).

## What it measures

A diagnostic agent begins with a brief 2–3 sentence case abstract (chief complaint + a few demographics). On each turn, the agent may:

1. **Ask questions** (free-text history or examination questions, *"Has she traveled recently?"*).
2. **Request diagnostic tests** (specific orders, *"Order CT chest with contrast"*).
3. **Commit to a final diagnosis** (one-shot).

The evaluation runs along **two axes**:

- **Diagnostic accuracy** — does the final diagnosis match ground truth? Scored on a 5-point Likert rubric (≥ 4 = correct, mirrors clinical-management-equivalence).
- **Cumulative cost** — sum of all diagnostic-test costs plus $300 per physician visit (multiple questions on one turn count as one visit). Test costs come from a 2023 U.S. health-system CPT pricing table.

This dual-axis framing connects directly to the **Triple Aim** (Berwick 2008): high-quality care delivered at sustainable cost.

## Why static-vignette benchmarks aren't enough

The paper's introductory argument: "Most diagnostic assessments present models with neatly packaged vignettes that bundle the chief complaint, history of present illness, key physical exam findings, and test results, and then ask the model to select a diagnosis from a predefined answer set. By reducing the sequential diagnosis cycle to a one-turn multiple-choice quiz, static benchmarks risk overstating model competence and obscure potential weaknesses including premature diagnostic closure, indiscriminate test ordering, and anchoring on early hypotheses."

This argument is the same one [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) makes about case-bench-vs-real-practice, and the same critique that motivated CRAFT-MD (vignette → conversation accuracy collapse), [healthbench](healthbench.md) (open-ended conversations), and [medagentbench](medagentbench.md) (FHIR EHR actions). SDBench's specific contribution: keep the *richness* of NEJM CPC cases while forcing the agent to *iteratively decide* what to do next under explicit cost.

## The three innovations

### 1. Gatekeeper agent

An LLM (the paper uses **o4-mini**) that holds the full NEJM case file and reveals findings only when explicitly queried. The Gatekeeper:

- Refuses to provide diagnostic impressions, interpret test results, or hint that information would be unavailable in a real encounter.
- Withholds imaging until explicitly ordered.
- Discloses pathognomonic findings *only* when the exact confirmatory test is requested.
- Returns polite refusals to vague or overly broad requests.
- Mirrors the information-extraction challenge clinicians face reviewing medical records — removes spoilers and hindsight bias.

### 2. Synthetic findings

A significant fraction of test requests target details not present in the original published case. The team's *initial* strategy — responding "Not Available" — had a side effect: it implicitly signaled which queries were "off-path" and discouraged valid alternative reasoning. The fix: the Gatekeeper returns **realistic synthetic findings** (numerically/descriptively consistent with the rest of the case) with no indication they're synthetic. This preserves clinical realism while avoiding leakage of "missing data" hints.

A panel of physicians reviewed **508 Gatekeeper responses** (real + synthetic mixed); they flagged only 8 as potentially problematic, and **none were judged to have leaked the diagnosis** after group adjudication.

### 3. Judge agent with physician-authored rubric

An LLM judge (the paper uses **o3**) evaluates each submitted diagnosis using a 5-point physician-authored Likert rubric covering: (1) core disease entity, (2) etiology, (3) anatomic site, (4) specificity / qualifiers, (5) completeness. The rubric anchors:

| Score | Label | Anchor |
|---|---|---|
| 5 | Perfect / clinically superior | Clinically identical or strictly more specific |
| 4 | Mostly correct (minor incompleteness) | Core disease correct, minor missing qualifier; management unchanged |
| 3 | Partially correct (major error) | Right disease category, major specificity/etiology/site error |
| 2 | Largely incorrect | Superficial similarity only; would misdirect work-up |
| 1 | Completely incorrect | Wrong organ/system; would likely lead to harmful care |

A cutoff of ≥ 4 counts as correct.

**Validity:** in-house physicians independently scored all 56 test-set MAI-Dx diagnoses plus 56 human-generated diagnoses. After binarizing both physician and Judge scores, **Cohen's κ = 0.70** for the MAI-Dx set (vs human-vs-human κ = 0.87 on the same set). In 4 of 5 disagreement cases, physicians judged the Judge to be **overly strict** (correctly diagnosing what the Judge had marked incorrect) — implying reported MAI-DxO accuracy slightly *underestimates* true performance.

## Train/test split

The **56 most recent cases** (2024–2025, published *after* model training cutoffs) were held out as a hidden test set, never seen during development. Relative gains of MAI-DxO over off-the-shelf baselines are preserved on the test set — important methodological signal against overfitting / memorization.

## Why SDBench may matter beyond MAI-DxO

The benchmark and the orchestrator are **separable artifacts**. SDBench is, in principle, a substrate any team can run any diagnostic agent (or human) against. The methodological contributions — Gatekeeper-as-oracle, realistic-synthetic-findings, physician-rubric-validated LLM judge, dual-axis (accuracy + cost) — are reusable and don't depend on MAI-DxO's specific architecture.

The paper notes SDBench is **in the process of being submitted for external peer review with potential public release** as a benchmark. If SDBench lands publicly, it has a credible path to becoming a foundational sequential-diagnosis benchmark in 2026–27.

## Caveats / limitations (explicit in source)

- **Case-distribution skew**: NEJM CPC cases are curated for instructional difficulty. Real deployment populations include common, benign, healthy presentations. SDBench therefore **cannot measure false-positive rates** — a critical safety axis [noharm](noharm.md) explicitly targets.
- **No specialty representation**: only 304 cases total, drawn from a publication that selects for cases-too-hard-for-the-original-treating-team.
- **Cost is a first-order proxy**: omits invasiveness, time-to-result, wait times, authorization/reimbursement constraints, geographic variation, payer mix.
- **Judging captures clinical-substance equivalence** but not *full diagnostic precision*: the κ = 0.70 is good-but-not-perfect.
- **Physician comparison is constrained**: participants explicitly forbidden external resources (no search, no LLMs, no EHR, no colleagues). This is the standard NEJM-cases-online problem (you have to prevent participants from googling the answer), but it makes the 19.9% physician baseline a **floor**, not a deployment-realistic figure.

## Cross-references

- [mai-dxo](../entities/mai-dxo.md) — the orchestrator built on top of SDBench.
- [agentic-clinical-ai](agentic-clinical-ai.md) — where MAI-DxO sits in the multi-agent literature.
- [llm-clinical-reasoning](llm-clinical-reasoning.md) — broader case-bench-vs-real-practice context.
- [clinical-validation](clinical-validation.md) — SDBench is an interesting middle layer: more realistic than static vignettes, less realistic than prospective deployment trials.
- [healthbench](healthbench.md), [medhelm](medhelm.md), [medagentbench](medagentbench.md), [noharm](noharm.md) — adjacent 2025 benchmark cohort.

## Sources
- [mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md) (Sections 2, 3.1, 3.3 — primary citation)
