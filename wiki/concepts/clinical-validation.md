---
type: concept
title: Clinical validation of medical AI
added: 2026-05-10
updated: 2026-05-10
sources: [[[ai-index-2026]]]
tags: [evaluation, governance, prospective-trial, evidence]
---

# Clinical validation of medical AI

The central evidence tension in 2025 medical AI: deployment is accelerating much faster than the rigorous evidence base. Most published clinical AI evaluations are not done on real patients — they are done on **exam-style questions, retrospective benchmarks, or curated case series**.

## The headline finding (2026)

The Stanford-Harvard [[arise-network]]'s inaugural *State of Clinical AI Report* (January 2026) reviewed **over 500 clinical AI studies** and concluded:

- **~half** relied on exam-style questions (e.g., USMLE-style, NEJM clinicopathological cases) rather than real patient data.
- **Only 5%** used real clinical data.
- The report's overall conclusion: AI performs most effectively when **supporting rather than replacing** clinician judgment.

A separate peer-reviewed analysis ([Singh et al., 2025](https://www.bmj.com/)) of 1,016 FDA AI/ML device authorizations through Dec 2024 found that **only 2.4%** of devices with clinical studies were supported by randomized controlled trial data, with nearly all entering via the [[fda-510k-pathway]].

## What "validation" can mean (gradient of rigor)

| Level | What it tests | How common in 2025 |
|---|---|---|
| Exam-style Q&A (e.g., USMLE) | Knowledge recall on standardized prompts | ~half of 500+ studies (ARISE) |
| Retrospective benchmark on curated images | Ability to match reference labels on past data | Dominant in imaging AI publications |
| Reader study with clinicians | Clinician-AI pair vs. clinician-alone, retrospective | Used for many FDA submissions |
| Prospective clinical trial | AI evaluated on live patient data with predefined endpoints | 536 imaging-AI papers in 2025 (up 28.5% YoY from 417) |
| RCT with patient outcomes | Direct comparison with randomization | Rare; only 2.4% of devices |

## The narrow-tool vs. open-LLM distinction

The 2026 AI Index makes a crucial framing point. Evidence-base concerns apply most sharply to **general-purpose LLMs in open-ended clinical reasoning** — see [[ai-hallucination-medical]] and the NOHARM benchmark (11.8–14.6 severely harmful recommendations per 100 cases for top LLMs, 76.6% errors of omission).

By contrast, **narrow tools operating in constrained workflows with clinician oversight have generated much stronger real-world evidence**:
- [[ambient-ai-scribes]] — multiple multi-site outcomes papers in 2025 ([[abridge]] deployment).
- AI sepsis prediction — [[trews]] and COMPOSER reported absolute mortality reductions in prospective deployments.

This distinction shows up repeatedly in governance frameworks (FURM, GUIDE-AI Lab) and is likely to be a load-bearing organizing principle for the wiki.

## Notable 2025 prospective clinical trials cited

- **MASAI** — randomized study of AI-assisted mammography reading (screening accuracy).
- **NOTIFY-1, NOTIFY-EXTEND** — tested whether flagging early signs of heart disease that AI spotted on routine CT scans changed clinician behavior (preventive cholesterol prescription).

The growth from 417 (2024) → 536 (2025) prospective imaging trial papers is a good proxy for the maturation of the field — but baseline volume is still small relative to the >5,000 medical AI papers published in 2025.

## Governance frameworks

- **Stanford Health Care's FURM framework** — governs all new AI tool adoptions at the institution.
- **GUIDE-AI Lab** — working to make FURM available to other health systems.
- See also general RAI standards being adopted in healthcare: NIST AI RMF, ISO/IEC 42001, EU AI Act high-risk obligations.

## Open questions

- How do "real clinical data" requirements get operationalized for foundation-model-based diagnostics, where pretraining data is sprawling and unverifiable?
- What's the FDA's evolving stance on Predetermined Change Control Plans (PCCPs) — used in ~10% of 2025 clearances — and how do they interact with post-market validation?
- Where are the dark spots — specialties with high adoption but minimal prospective evidence (e.g., parts of radiology, pathology)?
- What's the calibration story? AI may achieve high AUC but be poorly calibrated, leading to over/under-treatment downstream.

## Sources
- [[ai-index-2026]] (Ch. 6, p. 271, 273, 278, including ARISE box)
