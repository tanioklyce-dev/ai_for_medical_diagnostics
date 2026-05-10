---
type: concept
title: FDA 510(k) pathway for AI/ML medical devices
added: 2026-05-10
updated: 2026-05-10
sources: [../sources/ai-index-2026.md]
tags: [regulation/fda-510k, regulation/samd, deployment]
---

# FDA 510(k) pathway for AI/ML medical devices

The dominant U.S. regulatory route for AI/ML-enabled medical devices in 2025. **510(k) clearance** requires manufacturers to demonstrate that a new device is **substantially equivalent** to one already on the market — *not* that it has been validated via new clinical trials.

## Cumulative numbers (FDA, through Dec 2025)

| Metric | Count |
|---|---|
| Cumulative AI/ML-enabled devices cleared | **1,357** |
| Distinct manufacturers | **693** |
| Clinical specialties represented | **17** |
| Cleared in 2025 alone | **246** (imaging-related) / **258** (all) |
| 1,000-device milestone crossed | 2024 |
| New companies entering in 2025 | 98 (vs. 103 in 2023, 109 in 2024) |

The growth curve is steep and recent: just 16 imaging AI/ML devices were cleared in 2016. By 2023 the annual count was 218; 2024 was 222; 2025 was 246. The market is **concentrated at the top but fragmented overall** — of the 626 companies with ≥1 cleared device, the large majority hold only 1–2.

## By specialty (cumulative through 2025)

| Specialty | Devices | % |
|---|---|---|
| **Radiology** | **1,039** | **76.6%** |
| Cardiovascular | 130 | 9.6% |
| Neurology | 61 | 4.5% |
| Anesthesiology | 23 | 1.7% |
| Gastroenterology-Urology | 21 | 1.5% |
| Hematology | 20 | 1.5% |
| Ophthalmic | 10 | 0.7% |
| Clinical Chemistry | 9 | 0.7% |
| Pathology | 8 | 0.6% |
| Microbiology, GenSurg, Toxicology, Dental, Orthopedic, etc. | <10 each | — |

Non-radiology authorizations have grown from **7 in 2016 to 60 in 2025**. Cardiology, neurology, anesthesiology, and gastroenterology-urology have all seen acceleration since 2020 — AI is beginning to spread from imaging-centric applications into broader clinical domains.

## Top manufacturers (cumulative AI/ML cleared, 2016–2025)

1. **GE Healthcare** — 93
2. **Siemens Healthineers** — 82
3. **Shanghai United Imaging Healthcare** — 38
4. **Philips Healthcare** — 36
5. **Canon Medical Systems Corp** — 35
6. **Aidoc Medical, Ltd.** — 30
7. Samsung — 20; iSchemaView — 20
8. Hyperfine — 12; Viz.ai — 12
9. Clarius Mobile Health Corp. — 11
10. Brainlab — 10; Zebra Medical Vision — 9; RaySearch Labs (publ) — 8; Qure.ai Technologies — 8

## Evidence base under this pathway

The 510(k) pathway was designed to enable iteration on existing classes of devices — it relies on **existing safety and efficacy evidence rather than new RCTs**. Singh et al. (2025) analyzed all 1,016 authorizations through Dec 2024 and found:

- **Only 2.4%** of devices with clinical studies were supported by randomized controlled trial data.
- **Nearly all** devices entered via the 510(k) pathway (vs. De Novo or PMA).

This is the regulatory underpinning of the [clinical-validation](clinical-validation.md) tension.

## January 2025 FDA guidance on Total Product Life Cycle

In January 2025, the FDA issued draft guidance on AI-enabled device software functions applying a **Total Product Life Cycle (TPLC)** approach. A central mechanism: **Predetermined Change Control Plans (PCCPs)**, which permit iterative model updates after initial market authorization without requiring a fresh 510(k). PCCPs were used in **~10% of 2025 clearances** — a small but meaningful step toward governing continuously-updating AI.

## Open-source corner

**Comp2Comp** — a notable exception in a market dominated by commercial offerings. An open-source Python package for CT imaging analysis with two FDA-cleared modules (bone mineral density, abdominal aortic quantification) cleared in 2025.

## Key gap

**FDA clearance ≠ clinical adoption.** Financial, operational, and institutional barriers stand between regulatory authorization and real-world deployment. Healthcare systems typically require financial-clearance and cost-effectiveness justification before implementation. The cleared-device count is therefore a leading indicator of *availability*, not *use*.

## Related
- [clinical-validation](clinical-validation.md) — the evidence-rigor consequences of this pathway.
- [medical-imaging-ai](medical-imaging-ai.md) — the dominant use case for cleared devices.
- [ambient-ai-scribes](ambient-ai-scribes.md) — most scribes are *not* devices and bypass this pathway entirely.

## Sources
- [ai-index-2026](../sources/ai-index-2026.md) (Ch. 6.2, p. 273–276)
