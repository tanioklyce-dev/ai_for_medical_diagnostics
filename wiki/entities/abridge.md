---
type: entity
title: Abridge
added: 2026-05-10
updated: 2026-05-10
sources: [[[ai-index-2026]]]
tags: [organization/abridge, deployment, task/documentation]
---

# Abridge

The **leading ambient AI scribe platform** in 2025 by deployment breadth. Generates clinical documentation automatically from patient–clinician conversations.

## Adoption (2025)

- Expanded from **~100 to 150+ health systems**.
- Notable rollout: **Kaiser Permanente** — across **40 hospitals and 600+ medical offices**.
- Adoption reached **63% among hospitals using Epic's electronic health record system**.

## Outcomes documented across deploying institutions

Multi-site evidence (cited in the AI Index, all 2025):

- **Sharp HealthCare** — 83% reduction in note-writing effort; 3.5–6% increase in physician work RVUs per encounter.
- **University of Chicago Medicine** — 47% reduction in cognitive load; 58% increase in undivided patient attention.
- **MaineHealth** — 23% reduction in time on clinical notes; tool used in 70.3% of encounters.
- **Northwestern Medicine** — 11.3 additional patients per month; 24% reduction in documentation time; **112% ROI**.
- **Stanford Health Care** (JAMIA, Feb 2025) — prospective study of 48 physicians; statistically significant reductions in task load and burnout; median **20-minute time savings per half day of clinic**.

## Why Abridge sits at the center of the 2025 clinical AI story

The AI Index uses ambient scribes to draw a key contrast (Ch. 6.2, p. 278): narrow tools operating in **constrained workflows under clinician oversight** have generated strong real-world evidence, while general-purpose LLMs in open-ended clinical reasoning still produce concerning failure rates (NOHARM benchmark; see [[ai-hallucination-medical]]).

Abridge's deployment breadth, plus the consistency of multi-site outcomes, makes it the canonical example of clinical AI working in production.

## Adjacent vendors (not separately covered yet)

The AI Index doesn't enumerate Abridge competitors, but the ambient-scribe market includes:
- Microsoft DAX / Nuance
- Suki
- Ambience
- Heidi
- Augmedix

(These would be candidates for entity pages once a future source documents them.)

## What Abridge isn't

- **Not** an FDA-cleared medical device — scribes generally bypass [[fda-510k-pathway]] because they don't directly diagnose or treat.
- **Not** open-source.
- **Not** a diagnostic tool — though downstream AI tools acting on AI-generated notes is a domain to watch.

## Open questions / follow-up sources

- Patient-consent posture across U.S. states (the Mello et al. 2025 framework cited in Ch. 6.3 places ambient scribes in "notification" tier; some states require explicit consent legally).
- How does Abridge handle the [[ai-hallucination-medical]] / fabrication concern in note generation? What's the verification flow?
- Are productivity gains durable as physicians normalize to the tool?
- Pricing model and ROI variance across health system types.
- Outcomes for non-English-language encounters and underserved populations.

## Related
- [[ambient-ai-scribes]] — the category.
- [[clinical-validation]] — Abridge is the strongest evidence example for narrow workflow tools.
- [[ai-index-2026]] — primary source.

## Sources
- [[ai-index-2026]] (Ch. 6.2 Enterprise-Scale Deployments, p. 276–277)
