---
type: concept
title: LLM clinical reasoning
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [task/diagnosis, evaluation/benchmark, model-family/llm, model-family/foundation-model]
---

# LLM clinical reasoning

Recent reasoning-tuned LLMs (OpenAI o1-preview, o3, etc.) have **surpassed practicing physicians on benchmark clinical reasoning cases**. Whether this translates to better real-world outcomes is the open question, and depending on how it's posed it touches the heart of [clinical-validation](clinical-validation.md).

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

### Real emergency department cases (primary publication, 2025)

[ARISE 2026](../sources/arise-state-of-clinical-ai-2026.md) slide 18 cites **Brodeur, Buckley, Manrai, Rodman et al., ArXiv Jul 2025** as the primary source. In real ED cases, o1-preview achieved **66% exact-or-near-exact diagnoses** at initial triage, vs **48–54%** for physicians at the same touchpoint. Across three diagnostic stages (initial, post-history, post-workup), the model matched or outperformed attending physicians.

### The author's caveat
> "These results suggest that current LLMs have surpassed most existing clinical reasoning benchmarks, but they reflect isolated cognitive evaluations rather than real-world clinical integration. Whether AI-assisted reasoning translates to improved patient outcomes remains an open question requiring prospective trials."

This is the load-bearing caveat. The benchmarks are *case-bench style*, similar to what the [arise-network](../entities/arise-network.md) *State of Clinical AI* report flagged as evidence-thin.

## Multi-agent gains over single-agent baselines

Across published benchmark evaluations (Gorenshtein et al., Zheng et al., Liu et al., 2025), multi-agent frameworks showed diagnostic accuracy gains of **7% to over 60%** vs. single-agent baselines, depending on case complexity. The flagship example is **Microsoft's [mai-dxo](../entities/mai-dxo.md)** paired with OpenAI o3 — see that page for the comparable NEJM-case figure (80–85.5% vs. ~20% for 21 experienced physicians) plus the 70% cost reduction.

Other notable 2025 single-system reasoning results:
- **[amie](../entities/amie.md)** (Google): non-inferior to 21 PCPs in 100 three-visit simulated scenarios; outperformed PCPs on harder medication-reasoning RxQA. Multimodal AMIE outperformed PCPs on differential accuracy across 105 multimodal OSCE scenarios.
- **Dr. CaBot** (o3-based CPC discussant, Buckley et al. ArXiv Sept 2025): 60% top-1, 84% top-10 on CPC differential; physicians blindly rated its reasoning higher than human experts.
- **Script Concordance Testing** (McCoy/Rodman NEJM AI Sept 2025): o3 led at 68%, GPT-4o 64% — *matched students but below residents/attendings*. Reasoning models overuse extreme ratings, rarely select neutrality. A nuanced counterpoint to "AI > physicians."

## Suboptimal teaming and the human + AI question

ARISE explicitly raises whether "physician + AI > AI alone" — the **fundamental theorem of medical informatics** — actually holds:

- **Goh, Chen, Rodman et al., Nature Medicine Feb 2025**: in a 92-physician RCT, physicians + GPT-4 scored 43% vs **44% for the model alone** — no advantage to teaming. Indicates suboptimal HCI design, not AI ineffectiveness.
- **Everett, Horvitz et al., medRxiv Jun 2025**: a custom *collaborative* GPT-4 system with structured second-opinion / synthesis lifted accuracy from 75% (conventional) → 82% (AI second opinion) → 85% (AI first opinion). Did not exceed model alone (88%), but *raised the floor* by reducing low-scoring cases. Best evidence to date that good interface design beats raw model strength.
- **Liu, Chen et al., npj AI Dec 2025** (meta-analysis, 52 studies, 87 conditions): human + AI > human alone *on average*, but rarely achieves full complementarity (1+1≠2); often does not beat the best of the two. Junior clinicians benefit more from AI than seniors.
- **Qazi, Alizai medRxiv Jul 2025**: 20-hour AI-literacy training + GPT-4o lifted physician accuracy 43% → 71%. *Training matters.*

The picture: capability is no longer the bottleneck. Workflow design, training, and interface are. See [automation-bias-medical-ai](automation-bias-medical-ai.md) and [ai-deskilling](ai-deskilling.md) for the cautionary side of teaming.

## More deployment-realistic benchmarks

Benchmarks that step closer to deployment realism show much smaller AI advantage:

- **[medagentbench](medagentbench.md)** (Jiang et al., NEJM AI Aug 2025): evaluates LLM agents in a virtual FHIR EHR environment across **300 clinically derived tasks**. Best-performing model: **Claude 3.5 Sonnet 70%**, with 85% on queries but only 54% on actions.
- **[medhelm](medhelm.md)** (Bedi/Shah ArXiv Jun 2025): 35-benchmark suite, 12 use real EHR data. LLMs strongest on documentation (0.74–0.85) and patient communication (0.76–0.89), weakest on clinical decision support (0.61–0.76) and admin/workflow (0.53–0.63) — *exactly the tasks clinicians most want automated*.
- **2025 scoping review** identified 43 studies evaluating agentic AI in healthcare; 84% (36 of 43) were published in 2025 alone — i.e., the literature is brand new.

The takeaway: capabilities far outrun the validated evidence base, and as benchmarks get more realistic the gap narrows.

## What the benchmarks miss

- **Calibration**: high accuracy on selected cases doesn't speak to whether the model expresses appropriate uncertainty.
- **Belief vs. fact**: the [ai-hallucination-medical](ai-hallucination-medical.md) / KaBLE finding — GPT-4o's accuracy collapses from 98.2% to 64.4% when a false claim is framed as the user's first-person belief — is a directly diagnostic-relevant failure mode that case-style benchmarks don't capture.
- **Workflow integration**: clinical reasoning is interleaved with EHR navigation, ordering, prior-authorization paperwork, family communication — none of which appear in NEJM-style cases.
- **Liability and accountability**: who is responsible if an LLM-recommended diagnosis is wrong?

## Open questions

- Will reasoning-model gains translate to RCT-grade patient-outcome evidence, and on what timeline?
- Are these gains a feature of well-curated case-style cognitive tasks, or do they generalize to messy clinical practice?
- How do reasoning models behave on non-Western, non-English, or rare-disease cases not well represented in their training?

## Related
- [mai-dxo](../entities/mai-dxo.md) — Microsoft's multi-agent diagnostic system, the leading entity in this space.
- [agentic-clinical-ai](agentic-clinical-ai.md) — the broader category.
- [clinical-validation](clinical-validation.md) — the evidence-base context.
- [ai-hallucination-medical](ai-hallucination-medical.md) — the under-addressed failure mode.

## Sources
- [arise-state-of-clinical-ai-2026](../sources/arise-state-of-clinical-ai-2026.md) (Model Performance and Clinical Workflows sections — primary citation chain)
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2 highlight box on LLM Clinical Reasoning, p. 272; AI Agents box p. 272–273)
