---
type: source
title: Artificial Intelligence in Clinical Medicine — Challenges Across Five Domains (Ogut 2025)
authors: [Eren Ogut]
published: 2025-09-16
ingested: 2026-05-10
source_path: raw/clinpract-15-00169.pdf
url: https://www.mdpi.com/2039-7283/15/9/169
doi: 10.3390/clinpract15090169
journal: Clinics and Practice (MDPI)
volume: 15, 169
pages: 20
license: CC BY 4.0
tags: [broad-survey, evaluation/external-validation, modality/radiology, modality/pathology, task/diagnosis, governance]
---

# Artificial Intelligence in Clinical Medicine: Challenges Across Diagnostic Imaging, CDSS, Surgery, Pathology, and Drug Discovery (Ogut 2025)

> Single-author PRISMA-style review by Eren Ogut (Dept. of Anatomy, Istanbul Medeniyet University), MDPI *Clinics and Practice* Sept 2025. Synthesizes **150 studies** after screening 2,047 PubMed records across **five domains**: diagnostic imaging (n=74), clinical decision support (n=33), surgery (n=17), pathology (n=13), drug discovery (n=8), other (n=5). **Mostly confirms what we already have from [arise-state-of-clinical-ai-2026](arise-state-of-clinical-ai-2026.md) and [ai-index-2026](ai-index-2026.md) at much shallower depth**; valuable primarily as a *citation map* to a small number of underlying primary sources our wiki had not yet tracked.

## Summary

The review covers AI in clinical medicine across five domains and ten cross-cutting axes (the eleventh, "Future Integration," is forward-looking). Its central organizing claim — *"the most successful use cases involve human-AI collaboration rather than AI in isolation"* — is the same narrative ARISE 2026 documents with primary citations from 2024–2025, but Ogut traces it through older landmark papers (Gulshan 2016 diabetic retinopathy, Rajkomar 2018 EHR prediction, Rodriguez-Ruiz 2019 mammography, Attia 2019 Lancet AFib-from-ECG, Jumper 2021 AlphaFold, Försch 2021 pathology). The review's headline visuals are a structured-opinion **AI maturity scorecard across 11 axes** and a clustered **performance heatmap** comparing accuracy/AUC/sensitivity/specificity/clinical-impact across the five domains.

The most useful single contribution for this wiki is the **Vasey/JAMA Network Open 2021** primary citation: a systematic review of 37 ML-CDSS studies finding that *approximately half showed improvement, half showed no change or inconclusive results, and no clear improvement was observed in studies simulating real-world clinical settings.* This is the strongest pre-2025 primary citation for the CDSS-evidence-base gap that the more recent [Bedi/Shah JAMA Jan 2025 "5%" finding](../concepts/clinical-validation.md) reinforces — worth pulling forward as a primary citation in its own right.

Beyond that, the review surfaces familiar themes — black-box opacity, dataset-generalization brittleness, regulatory caution, ethical/legal liability uncertainty — without quantifying them or adding new primary evidence. ARISE 2026's [noharm](../concepts/noharm.md), MetaMedQA, CRAFT-MD, and NOTA findings all post-date this review's PubMed search and are more rigorous on the same concerns.

## Methodological caveats (worth keeping front-of-mind)

- **Simulated p-values.** The paper says: "Between-group comparisons were annotated with p-values, which were *derived from simulated hypothesis testing* to reflect domain-level significance." The maturity-score chart is a **structured opinion**, not statistical inference. Treat its rankings as suggestive, not evidentiary.
- **No formal risk-of-bias assessment.** The paper explicitly acknowledges Cochrane ROB tools were "not uniformly applied" given the diverse study designs. The author flags this as a limitation.
- **Single-author review** in a lower-tier MDPI journal, by an anatomist outside the core clinical-AI research community.
- **ChatGPT-assisted manuscript preparation.** Disclosed in acknowledgments: *"During the preparation of this manuscript, the author used ChatGPT (OpenAI, GPT-4o) for the purpose of language editing... The author has reviewed and edited all manuscript and takes full responsibility for the content of this publication."* Disclosure is up-front; treat normally per [arise-network](../entities/arise-network.md)'s bias-disclosure ethos, but worth knowing.
- **Citation generation seems uneven.** Some of the references (e.g., Ogut [9], [10], [33]) are the author's own prior work in unrelated areas (anatomy education, Kager's triangle, brain insula modeling), included as background citations in ways that don't always cleanly connect to the AI-in-medicine claims being made.
- **Pre-2025 evidence base.** The PubMed search appears to skew toward older landmark publications; the cohort of 2024–2025 prospective imaging RCTs that ARISE 2026 walks through (Vara MG, Brainomix 360, EyeFM, Penda AI Consult) is largely absent.

## Key claims and findings (what's worth pulling)

### AI maturity scorecard (Figure 2; structured opinion, 1–10 scale)

| Axis | Score |
|---|---|
| Diagnostic Imaging | 9.0 ± 0.6 |
| Human-AI Synergy | 9.0 ± 0.4 |
| Pathology | 8.0 ± 0.5 |
| Future Integration | 8.0 ± 0.5 |
| Clinical Decision Support | 7.0 ± 0.8 |
| Drug Discovery | 7.0 ± 0.6 |
| Regulation & Validation | 6.0 ± 0.6 |
| Surgical AI | 5.0 ± 0.7 |
| Explainability (XAI) | 5.0 ± 0.7 |
| Ethical & Legal Issues | 5.0 ± 0.8 |
| Bias & Data Issues | 4.0 ± 0.9 |

**Interpretation**: the scorecard ranks **deployment-stage technical performance high (imaging, pathology, human-AI teaming)** and **deployment-readiness concerns low (bias, explainability, ethics)** — consistent with the two-track field framing already in [overview](../overview.md). Useful as a coarse one-glance landscape map; not as evidence about any particular claim.

### Domain-specific findings worth pulling as primary citations

- **Vasey, Ursprung, Beddoe et al. *JAMA Network Open* 2021** — systematic review of **37 ML-CDSS studies**. Approximately half showed improvement, half showed no change or inconclusive results. **No clear improvement in studies simulating real-world clinical settings.** Pre-2025 primary for the CDSS-evidence-base gap; cite alongside Bedi/Shah JAMA Jan 2025 in [clinical-validation](../concepts/clinical-validation.md).
- **Försch, Klauschen, Hufnagl, Roth, *Dtsch. Arztebl. Int.* 2021** — pathologist sensitivity for lymph node metastasis detection **rose 83% → 91% when paired with AI** as second reader. Useful for the pathology section of [medical-imaging-ai](../concepts/medical-imaging-ai.md).
- **Mayo, Kent, Sen, Kapoor, Leung, Watanabe, *J. Digit. Imaging* 2019** — AI-augmented mammography CAD **reduced false-positive marks by 69%** vs traditional CAD. Pre-Vara-MG primary for the false-alarm reduction story.
- **Attia, Harrison, Lopez-Jimenez et al. *Lancet* 2019** — AI-ECG identifies patients with asymptomatic atrial fibrillation **during normal sinus rhythm** (retrospective analysis of outcome prediction). Precursor to the [echonext](../entities/echonext.md) / [present-shd](../entities/present-shd.md) opportunistic-ECG-screening paradigm.
- **Rajkomar, Oren, Chen et al. *npj Digital Medicine* 2018** — scalable deep learning on EHR data, accurate prediction of in-hospital mortality, readmission, and length of stay. Foundational primary for medical-event prediction; predates and motivates [delphi-2m](../entities/delphi-2m.md) and [comet](../entities/comet.md).
- **Gulshan et al. *JAMA* 2016** — deep learning detection of diabetic retinopathy in retinal fundus photographs (sensitivity comparable to ophthalmologists). Foundational primary citation.
- **Jumper et al. *Nature* 2021** — AlphaFold accurate protein structure prediction (already covered in our [alphafold-3](../entities/alphafold-3.md) lineage).
- **Ibrahim, Liu, Rivera et al. *Trials* 2021** — **CONSORT-AI** and **SPIRIT-AI** reporting-guideline extensions for AI clinical trials. Worth tracking as the methodology standard that should govern future prospective deployment trials.

### Performance heatmap (Figure 4)

Clustered heatmap of accuracy / AUC / sensitivity / specificity / clinical-impact across the 5 domains. Selected values (for reference):

| Domain | Accuracy | AUC | Sensitivity | Specificity |
|---|---|---|---|---|
| Radiology | 0.87 | 0.92 | 0.99 | 0.95 |
| Surgery | 0.80 | 0.84 | 0.99 | 0.97 |
| CDSS | 0.83 | 0.92 | 0.81 | 0.97 |
| Pathology | 0.84 | 0.89 | 0.86 | 0.90 |
| Drug Discovery | 0.92 | 0.87 | 0.83 | 0.86 |

These look like rough averages across the included studies and should be treated accordingly; the ARISE 2026 per-study breakdowns are the proper-evidence version.

### Cross-cutting themes (already covered by ARISE / AI Index more rigorously)

- **Black-box transparency** — known [ai-hallucination-medical](../concepts/ai-hallucination-medical.md) / Med-PRM / SourceCheckup territory.
- **Dataset generalization** — "models trained on data from one hospital may not generalize well to another." See [medical-imaging-ai](../concepts/medical-imaging-ai.md) data-scarcity and generalization-haircut discussion.
- **Regulatory caution** — see [fda-510k-pathway](../concepts/fda-510k-pathway.md).
- **Liability uncertainty** — open question, no resolution offered.
- **Workforce concerns** (will AI replace radiology techs, junior analysts) — speculative.

### Future-directions claims

- **Multimodal AI** combining imaging + clinical text + genomics (now realized in 2025 systems like MUSK, MOME, AMIE-multimodal — see [medical-imaging-ai](../concepts/medical-imaging-ai.md) and [amie](../entities/amie.md)).
- **Continuous learning systems** with safeguards against drift (Predetermined Change Control Plans under the [fda-510k-pathway](../concepts/fda-510k-pathway.md) are the current regulatory mechanism).
- **Federated learning** for cross-institutional training without data sharing (active research area; this review doesn't track specific 2024–2025 implementations).

## Entities and concepts touched

No new entity / concept pages created from this ingest. Light updates filed to existing pages where Ogut's referenced primary citations fill gaps:

- [clinical-validation](../concepts/clinical-validation.md) — added Vasey 2021 ML-CDSS systematic review reference + CONSORT-AI / SPIRIT-AI mention.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — added Försch 2021 pathology AI-pair sensitivity boost + Mayo 2019 mammography CAD false-positive reduction.

## Notes

- **Citation precedence on the synthesis story**: where Ogut and ARISE 2026 cover the same ground, **prefer ARISE** — primary citations, more recent, more rigorous methodology.
- **Use Ogut for**: the older landmark-paper citation chain (2016–2021), the structured-opinion maturity scorecard as a one-glance landscape view, and the Vasey 2021 / Försch 2021 / Mayo 2019 / CONSORT-AI primary citations not surfaced by ARISE.
- **Don't use Ogut for**: methodological strength claims (the simulated-p-values footnote is a real concern), or as the single-best-source for any specific finding — there's almost always a stronger primary citation available.
- **Future direction for the wiki**: if Vasey 2021 turns out to be widely cited and methodologically sound on independent review, it deserves to be promoted to its own primary-source page. Same logic for the CONSORT-AI / SPIRIT-AI reporting standards, which may warrant a concept page if/when more 2025–2026 trials adopt them.
