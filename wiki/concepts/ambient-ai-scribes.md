---
type: concept
title: Ambient AI scribes
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [deployment, task/documentation, evaluation/prospective-trial, workflow]
---

# Ambient AI scribes

Tools that **automatically generate clinical documentation from patient–clinician conversations**. The largest deployed category of clinical AI in 2025 by adoption breadth and outcomes evidence — and the AI Index's headline example of clinical AI moving from pilots to enterprise scale.

## Why this category matters

The 2026 AI Index treats ambient scribes as the canonical example of *narrow tools operating in constrained workflows under clinician oversight* — see [clinical-validation](clinical-validation.md). Unlike open-ended diagnostic LLMs, scribes do one task, with a human review step, and their outputs sit in a structured EHR slot. The evidence base reflects that: multiple multi-site outcomes papers in 2025, with consistent results across institutions.

## Adoption (2025)

- **[abridge](../entities/abridge.md)** — leading platform — expanded from ~100 to **150+ health systems**.
- **Kaiser Permanente** — deployed across **40 hospitals and 600+ medical offices** (Abridge).
- **63% adoption** among hospitals using Epic's EHR system.

## Reported outcomes (multi-site)

| Health system | Reported outcomes |
|---|---|
| **Sharp HealthCare** | 83% reduction in note-writing effort; 3.5–6% increase in physician work RVUs/encounter |
| **University of Chicago Medicine** | 47% reduction in cognitive load; 58% increase in undivided patient attention |
| **MaineHealth** | 23% reduction in time on clinical notes; tool used in 70.3% of encounters |
| **Northwestern Medicine** | 11.3 additional patients/month; 24% reduction in documentation time; **112% ROI** (one health system) |
| **Stanford Health Care** | Prospective study (n=48 physicians) published in **JAMIA Feb 2025**: statistically significant reductions in task load and burnout; median **20-minute time savings per half day of clinic** |

The Sharp HealthCare RVU finding is especially notable — it directly translates note-time savings into measurable productivity gain rather than just self-reported burnout reduction.

## Why scribes "work" while open-ended LLMs raise concerns

The AI Index draws an explicit contrast in section 6.2 (p. 278). Findings about general-purpose LLM hazards (NOHARM benchmark: 11.8–14.6 severely harmful recommendations per 100 cases; see [ai-hallucination-medical](ai-hallucination-medical.md)) apply to **open-ended clinical reasoning tasks**, not narrow workflow-embedded tools. Scribes share several risk-mitigating properties:

- **Constrained workflow**: input scope is the live patient encounter; output scope is the documentation field.
- **Clinician oversight**: physician reviews and signs the note before it enters the chart.
- **Low-stakes per-output**: documentation errors are caught downstream; not directly diagnostic.
- **Verifiable comparison**: clinicians can compare AI-generated note vs. their own recollection.

These properties don't generalize cleanly to other clinical AI categories — see [llm-clinical-reasoning](llm-clinical-reasoning.md) and [agentic-clinical-ai](agentic-clinical-ai.md) for the more contested deployment terrain.

## Adjacent generative-AI clinical workflow tools

Briefly mentioned in the same section:
- **ChatEHR** (Stanford-affiliated) — plain-language patient-record summaries; 23,000 sessions across 1,075 trained users in three months; 60% automated prompts, 40% interactive interfaces.
- **OpenEvidence** — real-time evidence retrieval platform; reported adoption by **40% of U.S. physicians**.
- A JAMA Network Open Aug 2025 study evaluated AI tools generating plain-language explanations of lab/imaging/pathology results: 85% of 93 survey respondents found the tool user-friendly; 72% beneficial for lab results, 63% for imaging.

## Open questions

- **Diagnostic implications**: scribes summarize but don't diagnose — yet downstream AI tools acting on AI-generated notes could amplify documentation errors. What's the cumulative-error story?
- **Patient consent**: see Mello et al. (2025) framework cited in the AI Index — ambient scribe summaries fall in the "notification" tier (not "consent required") because the AI summarizes the clinician's own dictation, but some U.S. states legally require consent.
- Are productivity gains durable, or do they fade as physicians adapt and the AI's novelty wears off?
- Vendor concentration — Abridge dominance, plus DAX (Microsoft/Nuance), Suki, Ambience, Heidi, etc. — what's the differentiation, and where does FDA oversight land if/when scribes start nudging clinical decisions?

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2, p. 276–278; Mello framework p. 282)
