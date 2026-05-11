---
type: source
title: Neural Network Classification of Corneal Topography — Preliminary Demonstration (Maeda, Klyce, Smolek 1995)
authors: [Naoyuki Maeda, Stephen D. Klyce, Michael K. Smolek]
published: 1995-06
ingested: 2026-05-10
source_path: raw/1327.pdf
url: https://pubmed.ncbi.nlm.nih.gov/7775110/
journal: Investigative Ophthalmology & Visual Science (IOVS)
volume: 36(7), 1327–1335
pages: 9
license: not specified (copyright Association for Research in Vision and Ophthalmology, 1995)
tags: [modality/ophthalmology, task/screening, task/classification, model-family/neural-network, historical]
---

# Neural Network Classification of Corneal Topography — Preliminary Demonstration (Maeda, Klyce, Smolek 1995)

> Self-described as *"to our knowledge, the first report of the successful application of a neural network model to classify corneal topography."* The [stephen-klyce](../entities/stephen-klyce.md) group's rung-three paper, published one year after the 1994 expert system and using **the same topographic indices as inputs** but replacing the rule-tree classifier with a backpropagation neural network. *Investigative Ophthalmology & Visual Science* 36(7):1327–1335, June 1995. Supported by US PHS NEI grants EY03311 and EY02377 (continuous from the 1984 paper) plus equipment support from Computed Anatomy (NY) and Menicon (Nagoya, Japan).

## Summary

The paper directly extends [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md). Where the 1994 work used **linear discriminant analysis + Pascal binary decision tree** over 8 topographic indices to classify 4 keratoconus-related categories, this paper uses an **11-index input → 18-hidden-neuron → 7-output-category multilayer perceptron** trained by backpropagation (Rumelhart/Hinton/Williams 1986). The seven categories expand to: normal, with-the-rule astigmatism, mild / moderate / advanced keratoconus, post-photorefractive keratectomy, and post-keratoplasty.

183 TMS-1 videokeratoscope maps were divided 108 / 75 for training and test. Eleven indices (the 1994 set — SimK1, SimK2, MinK, SAI, SRI, DSI, OSI, CSI, IAI, AA — plus a new **Standard Deviation of Power (SDP)** introduced in this work) form the input layer. Implementation: Brainmaker Professional v2.53 on an 80486 PC. Training converged in 1,509 iterations.

**Results.** Training accuracy 100% (108/108). Test accuracy 80% (60/75). Per-category accuracy and specificity >90%; sensitivity varied widely (44% advanced keratoconus → 100% post-PRK). The 80% test accuracy is comparable to contemporary neural-network applications to cancer diagnosis (80%) and glaucoma visual-field interpretation (65%). The authors explicitly note overfitting (training 100% vs. test 80%, χ² *p* = 0.0001) and recommend further work on input parameters, architecture, and dataset size. They frame the result as a **preliminary demonstration**, not a clinical-ready system — the 1997 follow-up ([smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md)) closes that gap.

## Key claims and findings

### Architecture (Figures 1, 2)

3-layer feedforward backpropagation network, fully connected:

| Layer | Size | Content |
|---|---|---|
| Input | 11 neurons | SimK1, SimK2, MinK, SAI, SRI, DSI, OSI, CSI, IAI, AA, SDP |
| Hidden | 18 neurons | sigmoid transfer function |
| Output | 7 neurons | normal, with-the-rule astigmatism, KC1 (mild), KC2 (moderate), KC3 (advanced), post-PRK, post-keratoplasty |

Hyperparameters: learning rate 100%, smoothing 0.9, single hidden layer. Training tolerance 0.1 (output ∈ {[0.9, 1.0] for correct category} ∪ {[0.0, 0.1] for incorrect categories}). Test threshold relaxed to 0.5 (winner-take-all); maps with no output ≥ 0.5 classified as "unknown pattern."

### New index introduced: SDP

**Standard Deviation of Power (SDP)** — standard deviation of the area-corrected corneal power array. New in this work and shown to have significant weight in the trained network. SDP is preserved as one of the 10 input indices in [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md).

### Validation results (Tables 5, 6)

| Category | n | Sensitivity | Specificity | Accuracy |
|---|---|---|---|---|
| Normal (NRM) | 12 | 83% (10/12) | 98% | 96% |
| With-the-rule astigmatism (AST) | 11 | 82% (9/11) | 97% | 95% |
| Mild keratoconus (KC1) | 8 | 63% (5/8) | 97% | 93% |
| Moderate keratoconus (KC2) | 12 | 92% (11/12) | 98% | 97% |
| **Advanced keratoconus (KC3)** | 9 | **44% (4/9)** | 98% | 92% |
| Post-photorefractive keratectomy (PRK) | 11 | 100% (11/11) | 100% | 100% |
| Post-keratoplasty (KP) | 12 | 83% (10/12) | 95% | 93% |
| **Overall** | **75** | — | — | **80% (60/75)** |

Misclassification patterns: three advanced-keratoconus maps interpreted as post-keratoplasty (and vice-versa) — a clinically plausible confusion since both feature localized abnormal steepening + reduced analyzed area. Two mild-keratoconus maps classified as astigmatism. Five maps classified as "unknown."

### Methodological framing vs. discriminant analysis vs. expert systems

Discussion explicitly compares the three approaches the same group has now used in sequence — **multivariate (discriminant) analysis** (1994, refs 16, 14), **expert system** (1994, ref 16), and **neural network** (this paper):

> "Neural networks show a unique ability to detect features that are hidden in the input data but are not explicitly formulated as input. Neither multivariate analysis nor expert systems can use hidden relationships in the input data. Also, the learning process of the neural network is based solely on the data supplied; no information is required about relationships, rules, or other logic structures between input and output data, whereas the expert system involves an extensive set of rules, deductive decision making, and step-by-step logical operation."

This is the same methodological argument that drives every subsequent transition in clinical AI: hand-crafted features and rules → learned representations. The authors are making it explicitly, in 1995, within their own research line.

### Acknowledged limitations

- Overfitting: 100% training vs. 80% test, χ² *p* = 0.0001, attributed to "memorizing some unimportant features in the maps during the training process" — a recognizably modern framing in 1995.
- Small per-category test sets (8–12 maps); sensitivity numbers are unstable.
- Restricted input modality: the network sees the 11 engineered indices, not the raw color map; "the network has a set of input data that is different from (and possibly more limited than) the data acquired by human inspection."
- No validation against unseen disease categories.

## Why this paper matters

For this wiki:

1. **Rung-three primary citation.** Closes the loop on [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md): rung 1 (1984 topography), rung 2 (1994 expert system), **rung 3 (1995 neural network)**, rung 4 (2018-onward deep learning).
2. **Same group, three methodologies in twelve months.** The 1994 expert-system paper and the 1995 neural-network paper share two authors (Klyce, Smolek) and were submitted/published within 12 months of each other (1994 ARVO meeting → 1993 ISRK meeting presentations of preliminary results; manuscript submitted Sep 1994, published Jun 1995). The group transitioned from rule-based AI to neural-network AI within their own research line, in the same paper series, on the same TMS-1 instrument.
3. **Engineered features + neural network hybrid.** Modern deep learning would let the network learn features from raw maps; this 1995 work feeds engineered indices into the network — the in-between architecture characteristic of the 1990s. The same engineered indices (KPI/DSI/OSI/CSI/SAI/IAI) recur for decades after.
4. **Explicit methodological self-critique.** The authors acknowledge overfitting, small dataset, and feature-engineering bottleneck — concerns that read as current today, written in 1995.

## Notes

- **Same lineage of NIH funding** as the 1984 and 1994 papers (NEI grants EY03311 + EY02377), reflecting Klyce's 36-year continuous R01 (1972–2008; see [stephen-klyce](../entities/stephen-klyce.md)).
- **Brainmaker Professional v2.53.** California Scientific Software's commodity neural-network development tool on a 486-class PC; representative of how 1990s biomedical research groups operationalized neural networks before TensorFlow / PyTorch.
- **Test-set design.** Maps with "atypical topographic appearances" excluded from the study; the network is therefore validated against a curated set of canonical patterns and *not* against the messy real-world distribution it would face in deployment. This is an important caveat the paper does not flag.
- **Successor paper.** [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md) is the systematic validation that addresses several of this paper's open issues (larger dataset, dedicated keratoconus-suspect category, head-to-head comparison with KPI/Rabinowitz/SimK).
- **The chain of indices**: 1994 introduced DSI, OSI, CSI, IAI, AA (alongside SimK1, SimK2, SAI). 1995 adds **SDP**. 1997 reorganizes the index set and adds **SK1** (the steep axis of simulated keratometry as input). These engineered features now propagate into every later corneal-topography ML/DL system in the literature.

## Entities and concepts touched

- [stephen-klyce](../entities/stephen-klyce.md) — senior author; rung-three primary in his publication record.
- [keratoconus-screening-ai](../concepts/keratoconus-screening-ai.md) — rung 3 of the four-rung lineage.
- [medical-imaging-ai](../concepts/medical-imaging-ai.md) — ophthalmology imaging-AI section.
- [maeda-klyce-keratoconus-screening-1994](maeda-klyce-keratoconus-screening-1994.md) — direct rung-two predecessor.
- [klyce-computer-assisted-corneal-topography-1984](klyce-computer-assisted-corneal-topography-1984.md) — rung-one foundation.
- [smolek-klyce-keratoconus-detection-1997](smolek-klyce-keratoconus-detection-1997.md) — successor paper extending this work to systematic validation.
