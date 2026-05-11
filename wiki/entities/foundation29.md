---
type: entity
title: Foundation 29 (rare-disease AI nonprofit)
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/do-olmo-dxgpt-rare-disease-2024.md]
tags: [organization/nonprofit, rare-disease, deployment, organization/microsoft-adjacent, geography/spain]
---

# Foundation 29

Spanish nonprofit founded **2017** by **Julián Isla**, a Microsoft software engineer based in Madrid, after his son Sergio was diagnosed with **Dravet syndrome** following a 10-month diagnostic odyssey (initial misdiagnosis; 20 seizures in a single day before correct identification). The "29" in the name references global Rare Disease Day, observed on the 29th of February.

The organization's signature product is **[dxgpt](dxgpt.md)** (launched 2023), a free, web-based, GPT-4-backed clinical decision-support tool for rare-disease diagnosis. By 2025, DxGPT had **>500,000 users globally** (US, Europe, India, China) and was integrated into the **Madrid public healthcare system**, accessible to ~6,000 doctors, with two major Madrid hospitals scheduled for expanded deployment in 2025.

## Origin and Microsoft connection

After his son's Dravet diagnosis in the mid-2010s, Isla emailed Satya Nadella in **2017**, referencing Nadella's own public story about his son with cerebral palsy. Nadella responded within five minutes and connected Isla to Microsoft's AI healthcare teams. Foundation 29 was founded the same year.

Microsoft's ongoing role:
- **Azure cloud infrastructure** — annual grant covers compute and hosting.
- **Azure OpenAI Service** as the production LLM substrate; [dxgpt](dxgpt.md) runs on GPT-4o and o1 as of 2025.
- Regulatory and technological guidance.
- Future plan: introduce DxGPT to **Azure Marketplace** for global physician access.

Foundation 29 is a nonprofit independent of Microsoft, but the partnership is load-bearing for its compute economics and product reach.

## Research output

- **Primary**: [do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md) (do Olmo, Logroño, Mascías, Martínez, Isla; medRxiv 2024). 13-LLM rare-disease benchmark on synthetic Orphanet cases + RAMEDIS + PUMCH (RareBench). Code: <https://github.com/foundation29org/dxgpt_testing/>.
- **In progress** (per §5.1 of the preprint): "real-world clinical studies involving DxGPT with real doctors and human evaluators in different hospitals and healthcare systems."

## Why this matters for the wiki

Foundation 29 is one of a small number of organizations that have **moved an LLM-based diagnostic tool into real clinical deployment at scale** — the still-emerging third track in the wiki's [clinical-validation](../concepts/clinical-validation.md) framing. The other large-N exemplar is the Penda Health × OpenAI [ai-consult-penda](ai-consult-penda.md) deployment in Kenya. Where Penda is a single-vendor, RCT-grade, single-country case study, Foundation 29 represents a different deployment shape:

- **Free, public, web-served** rather than embedded in a single health system.
- **Nonprofit / patient-foundation-driven** rather than vendor-driven.
- **Spanish-language-first** for the Madrid public-system deployment.
- **Rare-disease-focused** vs Penda's general primary-care safety-net role.

Together they make a stronger case that the "LLM-as-real-care-copilot" category is more than one anomaly.

## Caveats

- The 2024 preprint is **not peer-reviewed**. Per the medRxiv banner: "should not be used to guide clinical practice."
- **No published outcomes data**: the half-million-user and 6,000-Madrid-doctor figures come from a Microsoft EMEA news feature, not from a peer-reviewed deployment study. Effects on diagnostic accuracy, time-to-diagnosis, or patient outcomes are not yet documented in the literature.
- DxGPT is **explicitly not a medical device** — positioned as decision support, not autonomous diagnosis. GDPR-compliant; reported to have passed ethics-committee evaluations at deploying hospitals (per the same feature article).

## Related
- [dxgpt](dxgpt.md) — the product.
- [rare-disease-diagnosis](../concepts/rare-disease-diagnosis.md) — the task context.
- [ai-consult-penda](ai-consult-penda.md) — the parallel deployed-LLM-copilot exemplar.
- [mai-dxo](mai-dxo.md) — the academic-benchmark counterpart from Microsoft research (orchestrated frontier-LLM diagnosis on NEJM CPCs; not deployed in patient care).

## Sources
- [do-olmo-dxgpt-rare-disease-2024](../sources/do-olmo-dxgpt-rare-disease-2024.md) — primary citation for evaluation methodology and authorship; secondary for organizational facts.
- Microsoft Source EMEA feature, *"A father's quest for diagnosis inspired a disruptive AI solution"*: <https://news.microsoft.com/source/emea/features/a-fathers-quest-for-diagnosis-inspired-a-disruptive-ai-solution/>
- DxGPT website (about us): <https://dxgpt.app/aboutus>
