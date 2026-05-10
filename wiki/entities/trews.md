---
type: entity
title: TREWS — Targeted Real-time Early Warning System
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [task/early-warning, deployment, organization/bayesian-health, organization/johns-hopkins]
---

# TREWS — Targeted Real-time Early Warning System

A deployed **AI sepsis prediction system** developed at Johns Hopkins University and commercialized by **Bayesian Health**. One of the strongest 2025 examples of clinical AI moving from pilot to multi-site enterprise deployment with measurable outcomes.

## Deployment scope

- Deployed across **13 Cleveland Clinic hospitals**.
- Origin: Johns Hopkins University academic research.
- Commercial vehicle: Bayesian Health.

## Reported outcomes (2025)

| Metric | Result |
|---|---|
| **Relative reduction in sepsis mortality** | **18.7%** |
| Reduction in median time to first antibiotic order | **1.85 hours** |
| Correct sepsis case identification rate | 82% |
| Clinician adoption rate | **89%** |
| Reduction in ICU utilization | 10% |

## Why TREWS is significant

Sepsis is the canonical use case for clinical early-warning AI:
- It's time-sensitive (every hour without antibiotics increases mortality).
- It's diagnosable from EHR-resident data (vitals, labs, notes) rather than requiring imaging.
- It has a clinical handoff loop where the alert prompts a clinician to evaluate.

TREWS is one of two systems the AI Index cites with **prospectively-deployed mortality outcomes** at scale. The other is COMPOSER (UC San Diego Health) — a deep learning model monitoring 150+ variables per patient that reported 17% reduction in sepsis mortality (1.9% absolute) across 6,217 admissions, ~50 lives saved annually, and a 5% increase in sepsis bundle compliance.

Together, TREWS and COMPOSER are evidence that **clinician-in-the-loop EWS systems can produce real-world mortality improvements** — distinct from the case-bench-only validation that dominates other clinical AI categories. See [clinical-validation](../concepts/clinical-validation.md) for the broader context.

## Mechanism (from the AI Index summary)

The AI Index doesn't go deep on TREWS' internals, but characterizes it as:
- A **machine-learning early warning system** for sepsis.
- Operates on real-time streaming EHR data.
- Generates alerts to bedside clinicians who then evaluate and act.
- The 89% clinician adoption rate is itself a noteworthy achievement — many clinical alerts suffer from alert fatigue and low engagement.

## Why this works (per the source's framing)

The AI Index frames TREWS, COMPOSER, and ambient scribes as exemplars of **narrow tools operating in constrained workflows under clinician oversight** — see [ambient-ai-scribes](../concepts/ambient-ai-scribes.md) and [clinical-validation](../concepts/clinical-validation.md). Sepsis prediction has a:
- **Defined input scope**: EHR data, real-time.
- **Defined output**: an alert (binary or scored).
- **Built-in oversight**: clinician evaluates and orders antibiotics or rules out.
- **Verifiable downstream signal**: did sepsis develop, did mortality improve.

This is why the evidence base is stronger here than for open-ended diagnostic LLMs — see [ai-hallucination-medical](../concepts/ai-hallucination-medical.md).

## Open questions / follow-up sources

- The primary publications on TREWS deployment outcomes (Bayesian Health / Johns Hopkins) — should be ingested to verify and contextualize the figures.
- How does TREWS handle population shift across the 13 Cleveland Clinic hospitals (different demographics, EHR usage patterns)?
- What's the false-alarm rate, and how was alert fatigue managed to maintain 89% adoption?
- Is TREWS FDA-cleared as a medical device, or does it operate under a different regulatory framing?
- Calibration over time — does drift necessitate retraining cadence?

## Related
- [clinical-validation](../concepts/clinical-validation.md) — TREWS is a positive example of real-world evidence.
- [ambient-ai-scribes](../concepts/ambient-ai-scribes.md) — the other narrow-tool exemplar.
- [fda-510k-pathway](../concepts/fda-510k-pathway.md) — relevant if/when TREWS pursues device clearance.
- [ai-index-2026](../sources/ai-index-2026.md) — primary source.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2 Enterprise-Scale Deployments — AI-Powered Sepsis Prediction, p. 277)
