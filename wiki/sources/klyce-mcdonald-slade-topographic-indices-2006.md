---
type: source
title: Using Corneal Topographic Indices (Klyce, McDonald, Slade 2006)
authors: [Stephen D. Klyce, Marguerite B. McDonald, Stephen S. Slade]
published: 2006-10
ingested: 2026-05-10
source_path: raw/CRST1006_06.pdf
journal: Cataract & Refractive Surgery Today (CRST)
volume: October 2006, 58–60
pages: 3
license: not specified (copyright Bryn Mawr Communications / CRST, 2006)
tags: [modality/ophthalmology, task/screening, task/classification, model-family/expert-system, model-family/neural-network, deployment]
---

# Using Corneal Topographic Indices (Klyce, McDonald, Slade 2006)

> A practitioner-facing CRST cover story that documents the **commercial deployment** of the [stephen-klyce](../entities/stephen-klyce.md) group's screening indices in **three competing commercial corneal topographers by 2006** — the Tomey Keratoconus Screening Software (KCI from [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) and KSI from [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md)), the Humphrey/Zeiss Pathfinder, and the **Nidek Corneal Navigator (a deployed neural-network classifier)**. *Cataract & Refractive Surgery Today*, October 2006, pp. 58–60. Supported by NEI grants EY03311 and EY02377 (continuous Klyce-PI funding).

## Summary

By 2006, the engineered indices from the 1984/1994/1995/1997 Klyce-group lineage had crossed the research-to-deployment threshold and were running in the screening software shipped on three different commercial videokeratographers used in clinical refractive-surgery practice. This article — a peer-reviewed cover story in a clinician-facing periodical, authored by Klyce alongside two practicing refractive surgeons (McDonald and Slade) — instructs cataract and refractive surgeons on how to read these AI-derived indices in clinical context.

Three commercial systems are documented with example clinical screenshots:

| System | Manufacturer | AI machinery | Wiki citation |
|---|---|---|---|
| **Tomey Keratoconus Screening** | Tomey Corporation (Nagoya, Japan) | KCI (Klyce/Maeda 1994 expert system) + **KSI (Klyce/Smolek 1997 neural network)** running side-by-side | [1994](maeda-klyce-keratoconus-screening-1994.md), [1997](smolek-klyce-keratoconus-detection-1997.md) |
| **Humphrey Pathfinder** | Carl Zeiss Meditec (Dublin, CA) | Central Irregularity Measure (CIM), Shape Factor, Mean Toric K — color-coded against population thresholds | Carl Zeiss commercial |
| **Nidek Corneal Navigator** | Nidek Inc. (Fremont, CA) | "**Neural network-based system**" classifying normal / astigmat / keratoconus suspect / pellucid marginal degeneration / penetrating keratoplasty / myopic refractive surgery / hyperopic refractive surgery, with unknown variations classified as "other" | Nidek commercial; Klyce/Karon/Smolek 2005 *J Refract Surg* (cited ref 7) |

All three systems use the same **color-coded variance display** convention (green = normal, yellow = 2–3 SD from normal, red = >3 SD from normal) — a clinical-UI pattern derived from the 1984 [klyce-computer-assisted-corneal-topography-1984](klyce-computer-assisted-corneal-topography-1984.md) color-coded contour-map standard that Klyce participated in defining as the ANSI Corneal Topography Standard 1994–1998.

## Key claims and findings

### The screenshots are commercial deployment evidence

The Tomey Keratoconus Screening display (Figure 1) shows **the 1994 KCI and 1997 KSI running in parallel on the same patient**, both flagging the case as "Clinical Keratoconus Interpreted" with 70.1% Klyce/Maeda KCI similarity and 64.3% Smolek/Klyce KSI severity. Related indexes shown on the same display: SimK1 = 47.03, SimK2 = 43.76, CYL = 3.28, SAI = 2.38, DSI = 8.75, SRI = 0.91, OSI = 9.67, CSI = 0.37, SDP = 3.05, IAI = 0.46, KPI = 0.54, AA = 68.3%. **Every one of these indices originates in the 1994 or 1995 Klyce-group papers** (KPI, DSI, OSI, CSI, IAI, AA, SAI, SimK1, SimK2 from 1994; SDP from 1995); the entire commercial display is the operational realization of the rung-two and rung-three AI from the [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) lineage.

### Nidek's deployed neural network (Figure 3)

The Nidek Corneal Navigator caption explicitly states: *"This neural network-based system also classifies normals, astigmats, keratoconus suspects, pellucid marginal degeneration, penetrating keratoplasty, myopic refractive surgery, and hyperopic refractive surgery. Unknown variations are classified as other."* This is **a deployed clinical-grade neural-network classifier in routine ophthalmology practice in 2006** — eleven years after [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) and nine years after [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md). The deployment lag (research-to-clinical) is shorter than the lag often cited for general clinical AI (sometimes 17+ years).

### Klyce as Nidek paid consultant

The "About the Authors" section discloses: *"Stephen D. Klyce, PhD, is a Professor of Ophthalmology and Anatomy/Cell Biology at the Louisiana State University Health Sciences Center in New Orleans. He is a paid consultant to Nidek, Inc."* This is the direct research-to-industry pipeline by which the 1995–97 IOVS neural-network work entered the Nidek Corneal Navigator. (Reference 7 in this paper — Klyce SD, Karon MD, Smolek MK. *Screening patients with the corneal navigator.* J Refract Surg. 2005;21(suppl):617–22 — is the Klyce-authored primary description of the deployed Nidek system.)

### Forme fruste keratoconus (FFKC) framing

The paper's clinical thesis is that the AI-derived indices are **necessary but not sufficient** for diagnosing forme fruste keratoconus (FFKC) — a subclinical / early-keratoconus pattern that confers ectasia risk after LASIK but lacks the classic clinical signs. The 1994 KCI, 1997 KSI, Rabinowitz I-S, Klyce/Maeda KCI, and Nidek neural-network classifications are each presented with explicit caveats:

> "Although each of these tests is capable of estimating the likelihood of a given topography's being consistent with keratoconus suspects (or another corneal condition), it is essential for clinicians to realize that none is 100% specific, sensitive, or accurate. Practitioners must interpret the diagnostic information provided by the corneal topographer within the context of all the available clinical information."

This is a **2006 articulation of human-in-loop clinical AI framing** — the same framing the 2025–26 ARISE / FURM / FDA-510k literature ([clinical-validation](../concepts/clinical-validation.md), [arise-state-of-clinical-ai-2026](arise-state-of-clinical-ai-2026.md)) uses. Klyce's group was explicit about this position 20 years before it became the modern consensus.

### Practical clinical guidance on confounders

- Contact-lens-induced corneal warpage must stabilize before screening — soft-lens wearers may need *several weeks* of discontinuation before topography stabilizes (citing Wilson, Lin, Klyce et al. 1990 *Ophthalmology* 97:734–744, the [stephen-klyce](../entities/stephen-klyce.md) group's earlier primary work on contact-lens warpage).
- "There are no magic numbers; each case must be considered on its own merit and with an integrative evaluation of all the available clinical data."
- Confirmation strategy: repeat measurements of visual acuity, manifest refraction, and topography every 2–3 weeks until values stabilize before using AI indices for surgical planning.

## Why this paper matters

For this wiki:

1. **Commercial deployment evidence.** The 1994 KCI and 1997 KSI moved from research papers to deployed clinical software within ~9–12 years and were shipping in three competing commercial topographers by 2006. This is unusually fast research-to-deployment translation for medical AI; the wiki's general framing of clinical AI as slow-to-translate (5%-publication-to-deployment per [bedi-shah-pps-jama-2025](#) era statistics — see [clinical-validation](../concepts/clinical-validation.md)) does **not** apply to this lineage.
2. **2006 deployed neural network in ophthalmology.** The Nidek Corneal Navigator is **a deployed clinical neural-network classifier in 2006**, twelve years before the deep-learning wave broke into mainstream medical imaging. Documenting this in the wiki corrects a common framing that "clinical AI" began with Gulshan/Esteva 2016–17 deep-learning papers.
3. **Klyce-as-industry-consultant pipeline.** The paid-consultant disclosure documents how the 1995/1997 IOVS papers operationally entered the Nidek device. The 2025 Klyce CV adds that he was on the **Scientific Advisory Board of LENSAR 2010–2016**, **International Medical Advisory Board of Optical Express 2022–**, and continues to consult across the corneal-imaging industry. This is the mechanism by which the research lineage shaped commercial reality. (See [stephen-klyce](../entities/stephen-klyce.md).)
4. **Pre-FDA-clearance commercial deployment.** None of the three commercial AI screening systems described here were the subject of a separate FDA 510(k) clearance as an AI device — the videokeratoscope was the regulated artifact, and AI was bundled in as software. The modern [fda-510k-pathway](../concepts/fda-510k-pathway.md) treats this differently; this paper is a window into the regulatory state of clinical AI in the mid-2000s.
5. **Human-in-loop framing is decades-old.** The 2006 paper's articulation of AI-indices-as-screening-tool-not-diagnosis is the same human-in-loop framing the 2025–26 era frames as modern best practice. Klyce-group authors made this argument explicitly in 2006 — predating the modern framing by two decades.

## Notes

- **Marguerite B. McDonald** (co-author) led the LSU refractive-surgery team that invited Klyce to join in the early 1980s; she performed the **first PRK in man** with the team Klyce developed corneal-topography systems for. Her co-authorship on this 2006 paper, 20+ years after their initial collaboration, reflects continuous clinical-research partnership.
- **Stephen S. Slade** (co-author) is a Houston refractive surgeon; co-author here as a representative practicing clinician. No financial interest disclosed.
- **Reference 4** in the paper — *Rabinowitz YS. Ectasia after laser in situ keratomileusis. Curr Opin Ophthalmol. 2006;17:421–426* — is the contemporary primary citation on post-LASIK ectasia and the reason FFKC screening matters operationally.
- **Reference 5** — Maeda/Klyce/Smolek/Thompson 1994 IOVS 35:2749–2757 — the [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) source ingested earlier.
- **Reference 6** — Maeda/Klyce/Smolek 1995 IOVS 36:1327–1335 — the [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) source ingested in this same batch. The paper directly cites both predecessor IOVS papers as the research basis for what is now commercial software.
- **Citation precedence.** This article is **secondary** for the 1994/1995/1997 IOVS results themselves (cite those primary sources). It is **primary** for the commercial-deployment evidence of those results in Tomey/Humphrey/Nidek systems and for the 2006 disclosed Klyce-Nidek consulting relationship.

## Entities and concepts touched

- [stephen-klyce](../entities/stephen-klyce.md) — first author; the research-to-industry consulting pipeline.
- [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) — commercial-deployment dimension of the four-rung lineage.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — pre-deep-learning era of deployed clinical imaging AI.
- [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) — KCI deployed in Tomey software documented here.
- [maeda-klyce-keratoconus-neural-network-1995](maeda-klyce-keratoconus-neural-network-1995.md) — Nidek neural-network ancestor work.
- [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md) — KSI deployed in Tomey software documented here.
- [clinical-validation](../concepts/clinical-validation.md) — 2006 human-in-loop framing predates the modern formulation.
- [fda-510k-pathway](../concepts/fda-510k-pathway.md) — pre-modern-AI-device-regulation deployment baseline.
