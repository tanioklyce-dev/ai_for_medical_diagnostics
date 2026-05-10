---
type: concept
title: LLM clinical reasoning
added: 2026-05-10
updated: 2026-05-10
sources: [[[ai-index-2026]]]
tags: [task/diagnosis, evaluation/benchmark, model-family/llm, model-family/foundation-model]
---

# LLM clinical reasoning

Recent reasoning-tuned LLMs (OpenAI o1-preview, o3, etc.) have **surpassed practicing physicians on benchmark clinical reasoning cases**. Whether this translates to better real-world outcomes is the open question, and depending on how it's posed it touches the heart of [[clinical-validation]].

## Brodeur et al. (2025) — the headline study

A multi-experiment evaluation of OpenAI's **o1-preview** on diagnostic reasoning, management reasoning, probabilistic reasoning, and real ED cases, with blinded expert scoring.

### Differential diagnosis on NEJM clinicopathological conferences (n=143)
- Correct diagnosis appeared in **78/80 (97.5%) of differentials**.
- **52% top-1 accuracy** (correct on first try).

### NEJM Healer cases (n=80; revised IDEA score)
| | Score (out of 80) |
|---|---|
| **o1-preview** | **78** |
| GPT-4 only | 47 |
| Attending physicians | 28 |
| Resident physicians | 16 |

### Management reasoning (Gray Matters cases)
Box-plot median scores:
- **o1-preview**: 86%
- GPT-4 only: 42%
- Physicians + GPT-4: 41%
- Physicians + conventional resources: 34%

### 76 real emergency department cases
o1-preview produced "exact / very close" diagnoses in **67%–83%** of cases across three diagnostic stages — **surpassing two attending physicians at each stage**.

### The author's caveat
> "These results suggest that current LLMs have surpassed most existing clinical reasoning benchmarks, but they reflect isolated cognitive evaluations rather than real-world clinical integration. Whether AI-assisted reasoning translates to improved patient outcomes remains an open question requiring prospective trials."

This is the load-bearing caveat. The benchmarks are *case-bench style*, similar to what the [[arise-network]] *State of Clinical AI* report flagged as evidence-thin.

## Multi-agent gains over single-agent baselines

Across published benchmark evaluations (Gorenshtein et al., Zheng et al., Liu et al., 2025), multi-agent frameworks showed diagnostic accuracy gains of **7% to over 60%** vs. single-agent baselines, depending on case complexity. The flagship example is **Microsoft's [[mai-dxo]]** paired with OpenAI o3 — see that page for the comparable NEJM-case figure (85.5% vs. ~20% for 21 experienced physicians).

## More deployment-realistic benchmarks

Benchmarks that step closer to deployment realism show much smaller AI advantage:

- **MedAgentBench** (Jiang et al., 2025): evaluates LLM agents in a virtual EHR environment across **300 clinically derived tasks**. Best-performing model: **69.7% task success rate**.
- **2025 scoping review** identified 43 studies evaluating agentic AI in healthcare; 84% (36 of 43) were published in 2025 alone — i.e., the literature is brand new.

The takeaway: capabilities far outrun the validated evidence base, and as benchmarks get more realistic the gap narrows.

## What the benchmarks miss

- **Calibration**: high accuracy on selected cases doesn't speak to whether the model expresses appropriate uncertainty.
- **Belief vs. fact**: the [[ai-hallucination-medical]] / KaBLE finding — GPT-4o's accuracy collapses from 98.2% to 64.4% when a false claim is framed as the user's first-person belief — is a directly diagnostic-relevant failure mode that case-style benchmarks don't capture.
- **Workflow integration**: clinical reasoning is interleaved with EHR navigation, ordering, prior-authorization paperwork, family communication — none of which appear in NEJM-style cases.
- **Liability and accountability**: who is responsible if an LLM-recommended diagnosis is wrong?

## Open questions

- Will reasoning-model gains translate to RCT-grade patient-outcome evidence, and on what timeline?
- Are these gains a feature of well-curated case-style cognitive tasks, or do they generalize to messy clinical practice?
- How do reasoning models behave on non-Western, non-English, or rare-disease cases not well represented in their training?

## Related
- [[mai-dxo]] — Microsoft's multi-agent diagnostic system, the leading entity in this space.
- [[agentic-clinical-ai]] — the broader category.
- [[clinical-validation]] — the evidence-base context.
- [[ai-hallucination-medical]] — the under-addressed failure mode.

## Sources
- [[ai-index-2026]] (Ch. 6.2 highlight box on LLM Clinical Reasoning, p. 272; AI Agents box p. 272–273)
