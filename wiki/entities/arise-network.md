---
type: entity
title: ARISE Network (Stanford-Harvard)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [organization/stanford, organization/harvard, governance, evaluation/external-validation]
---

# ARISE Network (Stanford-Harvard)

A Stanford / Harvard / Beth Israel Deaconess research network that publishes the annual *State of Clinical AI Report* and maintains the [noharm](../concepts/noharm.md) safety benchmark. The inaugural [State of Clinical AI Report 2026](../sources/arise-state-of-clinical-ai-2026.md) (released January 2026) is the most rigorous primary-source synthesis the field has, and is the spine of this wiki for clinical-AI evidence.

## Leadership

- **Ethan Goh** — Executive Director, ARISE Network. Director of the Stanford Healthcare AI Leadership Program; Associate Editor at *BMJ Digital Health & AI*; founding editorial board, *NEJM AI*.
- **Adam Rodman** — Investigator. Assistant professor at Harvard Medical School; Director of AI Programs at the Carl J. Shapiro Center; Associate Editor at *NEJM AI*.
- **Jonathan H. Chen** — Investigator. Stanford's inaugural Director for Medical Education in AI in the Division of Computational Medicine.
- **Peter G. Brodeur** — Co-author. Cardiology fellow at Beth Israel Deaconess (Harvard Medical School).

Plus a broader author team including Liam McCoy, David Wu, Priyank Jain, Rebecca Handler, Jason Hom, Laura Zwaan, Vishnu Ravi, Brian Han, Kevin Schulman, Kathleen Lacar, Kameron Black, Adrian Haimovich, **Eric Horvitz** (Microsoft), and Emily Tat.

## What ARISE does

A meta-evaluation function not previously performed systematically at this scale: **bibliometric and methodological reviews** of the clinical AI evidence base, plus **own benchmark construction** for safety-critical evaluation gaps.

Three core artifacts:

1. **Annual *State of Clinical AI Report*** — the synthesis document.
2. **[noharm](../concepts/noharm.md)** safety benchmark — 100 specialist consult cases, 4,249 management actions, 12,747 expert annotations, evaluating *severe-harm probability* across 31 LLMs.
3. **MAST (Medical AI Superintelligence Test)** vision — a leaderboard at `bench.arise-ai.org` aggregating performance and safety across clinically realistic tasks.

## Influential findings (drawn from the 2026 report)

| Finding | Primary source | Implication |
|---|---|---|
| **Only 5% of LLM-eval studies used real clinical data**; 95% used accuracy on knowledge MCQ; <0.5% studied admin tasks (billing, prescriptions); 16% studied fairness/bias/toxicity | Bedi/Shah JAMA Jan 2025 (n=519 studies, 2022–2024) | The published "AI matches/beats clinicians" narrative rests on cognitive-test benchmarks, not deployment evidence. See [clinical-validation](../concepts/clinical-validation.md). |
| **Severe harm in up to 22% of cases across 31 LLMs**; 77% of severe harms are errors of omission | NOHARM (Wu/Goh ArXiv Dec 2025) | LLM accuracy benchmarks correlate only moderately (R=0.61–0.64) with safety. "Knowing the answer" ≠ "won't harm the patient." |
| **691 FDA-cleared AI/ML medical devices (1995–2023), >95% via 510(k); ~50% omitted study design, 53% lacked sample size, <1% reported patient outcomes, 95% lacked demographic data, 91% lacked bias assessments** | Cited in ARISE 2026 slide 5 | The regulatory substrate is permissive. See [fda-510k-pathway](../concepts/fda-510k-pathway.md). |
| **Conclusion**: AI performs most effectively when **supporting rather than replacing** clinician judgment | Synthesis | Reinforces clinician-in-loop deployment; complicates autonomous-AI framings. |

## Independence and disclosures

The 2026 report explicitly states "**ARISE's research program is supported through grants and industry research partners. This report was prepared independently.**" Disclosures (slide 128) note that Goh consults for Google, OpenAI, Samsung Research America, Roche Diagnostics, Novartis, Hello Heart, Grow Care Inc, and Faculty Connection; Rodman receives funding from the Moore Foundation, Macy Foundation, NIH, ARPA-H, Google, and Google DeepMind. Several "demo" slides flag sponsorship (Grow Therapy explicitly marked as research partner; SAGE / Grow Therapy listed as sponsored). This is worth tracking when treating ARISE as primary citation.

## Significance

ARISE is operating at the meta-evaluation layer — measuring not whether AI works, but **whether the evidence claiming AI works is methodologically sound**, and whether deployed systems are safe in real-consult contexts. This is a maturing-field signal: medical research has long had similar meta-review infrastructure (Cochrane Collaboration, EQUATOR Network); ARISE is building the AI-specific equivalent. Stanford Health Care's **FURM framework** is the deployment-governance counterpart at one health system; the **GUIDE-AI Lab** is working to extend FURM elsewhere.

## Cadence and follow-up

- 2026 State of Clinical AI Report is the *inaugural* annual; expect a 2027 edition.
- Engagement programs: Stanford Computational Medicine Colloquia (weekly, free), Stanford Healthcare AI Leadership & Strategy Program (CME, May 2026), Generative + Agentic AI Online Course (Harvard/Stanford, Summer 2026).
- Public benchmark portal: `bench.arise-ai.org` (NOHARM + MAST leaderboard).
- Contact: klacar@stanford.edu.

## Related

- [State of Clinical AI 2026](../sources/arise-state-of-clinical-ai-2026.md) — the report itself.
- [noharm](../concepts/noharm.md) — ARISE's safety benchmark.
- [clinical-validation](../concepts/clinical-validation.md) — ARISE's central topic.
- [ai-hallucination-medical](../concepts/ai-hallucination-medical.md) — companion failure-mode evidence.
- [ai-index-2026](../sources/ai-index-2026.md) — Stanford HAI's broader survey, where ARISE findings are cited.
