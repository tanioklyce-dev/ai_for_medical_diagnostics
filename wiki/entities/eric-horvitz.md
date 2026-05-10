---
type: entity
title: Eric Horvitz
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/mai-dxo-sequential-diagnosis-2025.md, ../sources/arise-state-of-clinical-ai-2026.md]
tags: [person, organization/microsoft, governance, model-family/llm]
---

# Eric Horvitz

Microsoft's Chief Scientific Officer, longtime principal investigator on AI in medicine, and one of the few researchers whose career bridges the **expert-system / Bayesian-decision-theory era of medical AI (1980s–2000s)** with the **LLM / agentic clinical-AI era (2020s)**. Appears across the major 2025 clinical-AI threads tracked in this wiki: lead-author tier on the MAI-DxO paper, ARISE *State of Clinical AI 2026* contributor, MD/PhD background, and connecting back through decades of foundational diagnostic-decision-support work.

## Why he's a load-bearing node

He shows up at the intersections:

- **Microsoft AI** — coauthor on *Sequential Diagnosis with Language Models* ([mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md)), the [mai-dxo](mai-dxo.md) primary paper. Author list includes Microsoft AI's Mustafa Suleyman, Dominic King, Harsha Nori, and Horvitz.
- **[arise-network](arise-network.md)** — listed among the contributing authors to the *State of Clinical AI Report 2026*; brings the Microsoft + Stanford + Harvard threads together. ARISE explicitly thanks him in the acknowledgements section.
- **Collaborative AI workflow design** — coauthor on the Everett/Horvitz medRxiv June 2025 collaborative-GPT-4 RCT (custom interface lifted physician accuracy 75% → 82–85% as second/first opinion). One of the strongest 2025 demonstrations that interface design beats raw model strength. See [llm-clinical-reasoning](../concepts/llm-clinical-reasoning.md).
- **Historical roots** — the [mai-dxo-sequential-diagnosis-2025](../sources/mai-dxo-sequential-diagnosis-2025.md) references trace directly to his earlier work:
  - *Pathfinder* (Heckerman, Horvitz, Nathwani 1992) — Bayesian decision-theoretic expert system for pathology.
  - *Diagnostic strategies in the hypothesis-directed Pathfinder system* (Horvitz, Heckerman, Nathwani, Fagan 1984).
  - *Decision theory in expert systems and artificial intelligence* (Horvitz, Breese, Henrion 1988).
  - *Time-critical action: representations and application* (Horvitz, Seiver 1997).

The MAI-DxO paper's Section 5.2 explicitly cites these as the normative-Bayesian-decision-theory roots that the orchestrator's "Dr. Hypothesis" (probability-ranked differential with Bayesian update) and "Dr. Test-Chooser" (maximum information per dollar) descend from. **In other words: MAI-DxO is the 2025 LLM realization of a research agenda Horvitz has been pursuing since 1984.**

## Significance for the wiki

When a recurring author appears across what otherwise look like independent threads (Microsoft commercial agents, academic ARISE meta-evaluation, collaborative-interface RCTs, foundational Bayesian decision theory), it signals coordination at the level of research direction. For this wiki:

- Treat the MAI-DxO orchestrator's architectural details (Bayesian-updated differential, value-of-information-based test selection) as *not new ideas* but as **30-year-old normative principles finally instantiable in modern LLMs**.
- Treat ARISE's framing of "AI augments rather than replaces" as compatible with — not in tension with — Horvitz-led work on AI orchestrators, despite surface tension between "MAI-DxO outperforms physicians 4×" and "AI supports rather than replaces."
- Watch for future cross-pollination: collaborative-AI interface design (Everett 2025) + agentic orchestration (MAI-DxO) + safety benchmarking ([noharm](../concepts/noharm.md), ARISE) is the work program Horvitz appears to be steering across institutions.

## Open / follow-up

- The Brodeur Buckley Manrai Rodman 2024 paper (ArXiv 2412.10849, the primary o1-preview NEJM-CPC paper) doesn't list Horvitz, but the analytical framework (Bayesian differential, sequential test selection) it analyzes is downstream of his theoretical work.
- Look out for whether the FURM framework (Stanford Health Care's deployment-governance counterpart referenced by ARISE) has Microsoft-side ties — likely.
- Possible future pages: **Adam Rodman** (Harvard, NEJM AI Associate Editor, [arise-network](arise-network.md) leadership, *Bedside Rounds* podcast, recurring coauthor in this corpus) and **Jonathan H. Chen** (Stanford, Inaugural Director for AI in Medical Education, ARISE co-PI, automation-bias / EHR-AI work). Both currently referenced inline from the [arise-network](arise-network.md) entry; promotion to own pages is judgment call deferred.
