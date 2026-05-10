---
type: concept
title: AI hallucination in medical contexts
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [evaluation/factuality, concern/safety, model-family/llm, risk]
---

# AI hallucination in medical contexts

The tendency of LLMs to generate plausible but false information — and the directly diagnostic-relevant failure modes that case-style benchmarks miss. The 2026 AI Index treats hallucination/factuality as one of the few RAI dimensions where evaluation is maturing, and surfaces multiple medically-relevant findings.

## Hallucination rates across leading models (2025)

### AA-Omniscience benchmark (Artificial Analysis)
A knowledge and hallucination benchmark testing factual reliability across **6,000 questions in six domains** including law, **health**, software, math.

| Model | Hallucination rate |
|---|---|
| **gpt-oss-20B (high)** | **94%** |
| Gemini 3 Flash | 92% |
| GPT-5.4 mini (xhigh) | 90% |
| Llama 4 Maverick | 87% |
| Mistral Large 3 | 87% |
| DeepSeek V3.2 | 82% |
| Claude Opus 4.6 (max) | 65% |
| MiMo-V2 (Feb 2026) | 48% |
| Claude Sonnet 4.6 (max) | 46% |
| MiMo-V2-Pro | 30% |
| Claude 4.5 Haiku | 26% |
| **Grok 4.20 Beta 0305** | **22%** |

Hallucination rates **range 22%–94% across 26 top models**. Per-domain breakouts (Figure 3.2.7 in the report) show meaningful variation in **Health** specifically — a model that excels in software engineering may underperform in health, and vice versa.

### HHEM (Hughes Hallucination Evaluation Model, Vectara)
Measures hallucination rates when summarizing documents from CNN/Daily Mail. Top 15 models cluster in 1.8%–5.4% — a much narrower range, because the task (summarization with source documents) is more constrained than open-ended Q&A.

## The KaBLE belief-vs-fact finding (medically-explicit framing)

KaBLE (Suzgun et al., 2025) is a new benchmark designed to test whether language models can distinguish between what is **known** and what is merely **believed** — what the authors call epistemic reliability. **13,000 questions across 13 tasks; 24 leading LLMs.**

The AI Index frames this directly in medical-diagnostic terms:

> *"a model used to support a medical diagnosis based on a patient's mistaken belief, as opposed to an established fact, could reinforce an inaccurate diagnosis and treatment plan."*

The finding: model accuracy collapses when a false statement is framed as the user's first-person belief.

| Model | True facts (3rd person) | False beliefs (1st person) |
|---|---|---|
| GPT-4o | **98.2%** | **64.4%** |
| DeepSeek R1 | >90% | **14.4%** |
| Newer reasoning models (avg) | ~95% | 62.6% |
| Older models (avg) | ~79% | 52.5% |

When a user says "I believe I have X — am I right?" with a false premise, models tend to play along. This is **a directly diagnostic-relevant failure mode** — the kind of input a clinical LLM would get from a patient asking about their condition.

## NOHARM benchmark — primary 2025 numbers

[noharm](noharm.md) (Wu, Goh et al. ArXiv Dec 2025) is now ingested with full primary detail. Updated numbers from ARISE 2026:

- **Severe harm in up to 22% of cases across 31 LLMs** (the AI Index reported 11.8–14.6 per 100; NOHARM's own paper reports up to 22% severe harm in worst-case configurations).
- **77% of severe harms are errors of omission** (failing to recommend critical tests/treatments) — confirms and refines the AI Index's 76.6% number.
- Standard knowledge benchmarks correlate only moderately with NOHARM safety (R = 0.61–0.64) — **MedQA scores do not predict real consult safety.**
- Best LLMs outperform generalist physicians on NOHARM by ~10%.
- **Three-agent "advisor + guardian" systems show ~6× higher odds of top-quartile safety** vs solo models.

The narrow-tool vs open-LLM distinction still holds: these findings apply to general-purpose LLMs in open-ended consult tasks, *not* the constrained-workflow narrow tools (see [ambient-ai-scribes](ambient-ai-scribes.md), [trews](../entities/trews.md)).

## More 2025 fragility findings

- **MetaMedQA** (Griot, Yuskel et al. *Nature Communications* Jan 2025) — 12 LLMs, 0% recall recognizing unanswerable / malformed questions. Even GPT-4o (73% accuracy) gives maximum-confidence scores when correct answers are absent. **Disconnect between accuracy and confidence.**
- **CRAFT-MD** (Johri, Rajpurkar et al. *Nature Medicine* Jan 2025) — converted 2,000 static clinical vignettes to multi-turn natural dialogue. GPT-4 dropped 0.82 → 0.63; GPT-3.5 0.66 → 0.47. With multiple-choice options removed, GPT-4 fell to 0.49. **Models miss critical history details under conversation.**
- **"None of the other answers" (NOTA)** (Bedi, Shah et al. *JAMA Network Open* Aug 2025) — 100 MedQA questions modified so NOTA is the correct answer (68-item validated set). Frontier-model accuracy drops 9–38%. Models like DeepSeek-R1, o3-mini, Claude 3.5 Sonnet, Gemini 2.0 Flash, GPT-4o, Llama 3.3-70B all degrade. **Strong MCQ performance is partly pattern recognition.**
- **SourceCheckup** (Wu, Zou et al. *Nature Communications* Apr 2025) — 800 questions, ~50,000 statement–source pairs, 7 LLMs. **50–90% of LLM responses partly unsupported by their own cited references.** Even GPT-4o + RAG: only 55% response-level support; 30% of statements lacked backing. **Retrieval helps but isn't enough.**
- **The illusion of multimodal readiness** (Gu, Vozila et al. *ArXiv* Oct 2025) — leading multimodal medical models give correct answers above chance even when images are missing/perturbed, with high-confidence chain-of-thought hallucinating visual features that aren't there. **Shortcut learning, not visual grounding.**
- **Fine-tuning doesn't fix knowledge gaps** (Wu, Zou et al. *NEJM AI* Jul 2025) — fine-tuned six commercial LLMs on new medical knowledge (FDA approvals, EHRs, updated guidelines). Memorization 90%+, generalization to vignettes only 30% drugs / 12% EHR / 20% guidelines. **Fine-tuning ≠ teaching real reasoning.**

## The RAI tradeoff problem

Top takeaway #8 of the Responsible AI chapter: training techniques aimed at improving one RAI dimension **consistently degrade another**. Specifically: **safety tuning can reduce factual accuracy**. This is a critical issue for medical AI — heavy refusal training can make a model decline to answer legitimate clinical questions while not actually reducing hallucination on non-refused answers.

## Implications for medical AI deployment

1. **Don't extrapolate from non-medical hallucination scores.** Per-domain variation is large; a model that hallucinates 30% on average might be much worse in health.
2. **Scrutinize how models handle false patient premises.** The KaBLE finding suggests common test protocols (3rd-person fact recall) overstate real-world reliability.
3. **Operating envelope matters.** A model with 14% severe-harm rate on open-ended clinical reasoning can still be safe in a constrained workflow with mandatory clinician review (see [ambient-ai-scribes](ambient-ai-scribes.md)).
4. **Calibration > raw accuracy.** A model that appropriately says "I don't know" outperforms a confident liar — even at lower top-1 accuracy.

## Open questions

- Is the medical-domain hallucination penalty closing across model generations, or is it stable?
- How do RAG-augmented or retrieval-grounded systems (e.g., [abridge](../entities/abridge.md)-style architectures with document grounding) shift these numbers?
- What's the right benchmark for *clinical-context-sensitivity* — a model's ability to flag uncertainty proportional to clinical risk?

## Related
- [clinical-validation](clinical-validation.md) — broader evidence-base context.
- [llm-clinical-reasoning](llm-clinical-reasoning.md) — case-style benchmarks that miss this failure mode.
- [ai-index-2026](../sources/ai-index-2026.md) — primary source.

## Sources
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (Benchmarks & Evaluations + Foundational Methods sections, primary citations)
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 3.2, p. 134–138 — RAI benchmarks, HHEM, AA-Omniscience, KaBLE; Ch. 6.2 evidence gaps, p. 278 — NOHARM)
