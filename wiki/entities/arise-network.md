---
type: entity
title: ARISE Network (Stanford-Harvard)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [organization/stanford, organization/harvard, governance, evaluation/external-validation]
---

# ARISE Network (Stanford-Harvard)

A Stanford-Harvard consortium that publishes the *State of Clinical AI Report*. The inaugural report (January 2026) is the most-cited evidence-base critique in the AI Index 2026's Medicine chapter.

## What it is

A research network spanning Stanford University and Harvard. The ARISE Network produces **bibliometric and methodological reviews** of the clinical AI evidence base — a meta-evaluation function not previously systematically performed at this scale.

## *State of Clinical AI Report* — January 2026 (inaugural)

The report reviewed **over 500 clinical AI studies** and surfaced findings that have shaped the AI Index 2026's framing of the field:

| Finding | Implication |
|---|---|
| **~half of studies relied on exam-style questions** rather than real patient data | The published "AI matches/beats clinicians" narrative rests heavily on cognitive-test-style benchmarks |
| **Only 5% of studies used real clinical data** | Most clinical AI claims have not been validated against the actual deployment context |
| **Conclusion**: AI performs most effectively when **supporting rather than replacing** clinician judgment | Argues against autonomous-AI framings, in favor of clinician-in-the-loop deployment |

This is the single most influential finding cited in the AI Index 2026's Ch. 6 Evidence Gaps and Governance section (p. 278). It underpins the [clinical-validation](../concepts/clinical-validation.md) framing across the wiki.

## Companion: NOHARM benchmark

The AI Index discusses NOHARM alongside ARISE's findings (the report doesn't attribute NOHARM to ARISE specifically, but they share thematic territory):

- Top LLMs produced **11.8 to 14.6 severely harmful recommendations per 100 clinical cases**.
- **76.6% were errors of omission** (e.g., failing to recommend a critical test).
- These findings apply to **general-purpose LLMs evaluated on open-ended clinical reasoning**, not narrow task-specific tools.

See [ai-hallucination-medical](../concepts/ai-hallucination-medical.md) for full treatment.

## Significance

ARISE is operating at the meta-evaluation layer — measuring not whether AI works, but **whether the evidence claiming AI works is methodologically sound**. This is a maturing-field signal: medical research has long had similar meta-review infrastructure (Cochrane Collaboration, etc.); ARISE is building the AI-specific equivalent.

The AI Index suggests this kind of independent meta-evaluation is part of why governance frameworks are advancing in 2025–26. **Stanford Health Care's FURM framework** now governs all new AI tool adoptions at Stanford, and the **GUIDE-AI Lab** is working to make FURM available to other health systems — these are the governance counterparts to ARISE's evaluative function.

## Open questions / follow-up sources

- The full ARISE *State of Clinical AI Report* (Jan 2026) — should be ingested directly into `raw/` to verify the 5%/half-study figures and understand methodology.
- ARISE's planned cadence (annual? biennial?).
- Whether ARISE plans to maintain a public registry / database of clinical AI studies meeting their methodological bar.
- Connections to other meta-research infrastructure (Cochrane, EQUATOR Network, IDEAL framework).

## Related
- [clinical-validation](../concepts/clinical-validation.md) — ARISE's central topic.
- [ai-hallucination-medical](../concepts/ai-hallucination-medical.md) — companion failure-mode evidence.
- [ai-index-2026](../sources/ai-index-2026.md) — citing source.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2 Evidence Gaps and Governance, p. 278; Top Takeaway #12, p. 10)
