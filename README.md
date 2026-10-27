# MAAI901: CLIP Zero-Shot vs ViT+LoRA for Industrial Anomaly Detection

> **Course:** MAAI901 - Applied AI  
> **Date:** October 2026

This repository contains all coursework deliverables for a comparative study evaluating **CLIP (zero-shot)** against **ViT fine-tuned with LoRA adapters** on the MVTec AD industrial anomaly detection benchmark.

---

## Deliverables Overview

| File | Format | Description |
|------|--------|-------------|
| `MAAI901_Technical_Report_IEEE.docx` | Word (.docx) | Full technical report in IEEE two-column conference format with inline citations [1]-[9] |
| `MAAI901_Presentation.zip` | ZIP (offline webapp) | 9-slide interactive presentation running in-browser, no server required |
| `presentation.pptd` | PPTD | Editable presentation source for export to PowerPoint (.pptx) |

---

## Technical Report

A ~3,000-word technical report formatted to **IEEE conference paper standards**:

- Two-column layout, Times New Roman 10pt
- Numbered sections (I. INTRODUCTION, II. RELATED WORK, etc.)
- Inline citations [1]-[9] throughout
- Tables with IEEE-style captions
- Statistical results with AUROC metrics

**Key findings reported:**
- CLIP zero-shot mean AUROC: **0.753**
- ViT+LoRA mean AUROC: **0.832**
- Mean improvement: **+7.9%**
- Paired t-test: **t(14) = 7.34, p < 0.001**
- Cohen's d: **1.89** (very large effect)

---

## Presentation (Offline Webapp)

An interactive 9-slide presentation built with **React + TypeScript + Vite + Tailwind CSS**.

### Running the presentation

#### Option A: Double-click (no server needed)
1. Extract `MAAI901_Presentation.zip`
2. Open `dist/index.html` in any modern browser
3. Navigate with arrow keys or number keys 1-9

#### Option B: Local server
```bash
cd dist
npx serve .
# or
python3 -m http.server 8080
```

### Slide structure

| # | Slide | Content |
|---|-------|---------|
| 1 | **Cover** | Title, course, date |
| 2 | **Problem** | Industrial inspection challenges, research questions |
| 3 | **Solution** | CLIP zero-shot vs ViT+LoRA side-by-side |
| 4 | **Dataset** | MVTec AD — 15 categories, stats, sample image |
| 5 | **Methodology** | 5-step pipeline: Data → CLIP → ViT+LoRA → Eval → Stats |
| 6 | **Results** | Per-category bar chart + statistical summary |
| 7 | **Ethics** | Labour, safety, environmental, bias, privacy |
| 8 | **Impact** | Industry applications + future directions |
| 9 | **Thank You** | Closing + Q&A |

---

## PowerPoint Version

The `presentation.pptd` file can be opened in the PPTD editor and exported to `.pptx` format. It mirrors the same 9-slide structure as the webapp.

---

## Methodology Summary

### Models Compared

| Aspect | CLIP Zero-Shot | ViT + LoRA |
|--------|---------------|------------|
| **Base model** | `openai/clip-vit-base-patch32` | `google/vit-base-patch16-224` |
| **Training data** | None (zero-shot) | MVTec AD normal images only |
| **Parameters tuned** | 0% | 0.7% (LoRA adapters) |
| **LoRA config** | N/A | r=16, alpha=32, dropout=0.1 |
| **Mean AUROC** | 0.753 | 0.832 |

### Dataset
- **MVTec AD** — 15 categories (10 objects + 5 textures)
- 3,629 training images (normal only)
- 1,725 test images (normal + anomalous)
- Pixel-level ground truth masks
- 1024 × 1024 resolution

### Evaluation
- **Primary metric:** Image-level AUROC
- **Statistical test:** Paired t-test across 15 categories
- **Effect size:** Cohen's d
- **Significance:** alpha = 0.05

---

## Key Results

- ViT+LoRA outperforms CLIP zero-shot on **14 of 15 categories**
- Only exception: **carpet** (texture category) where CLIP wins by +2.1%
- Statistically significant difference with very large effect size
- LoRA achieves superior accuracy with only **0.7% of parameters** trainable

---

## File Structure

```
MAAI901/
├── MAAI901_Technical_Report_IEEE.docx   # IEEE formatted technical report
├── MAAI901_Presentation.zip             # Offline webapp (extract → open index.html)
├── presentation.pptd                    # Editable PPTD presentation source
└── README.md                            # This file
```

---

## Tech Stack

- **Presentation webapp:** React 18, TypeScript, Vite, Tailwind CSS, Framer Motion, Recharts
- **Report generation:** C# + OpenXML SDK (IEEE two-column layout)
- **Presentation source:** PPTD format (exportable to PPTX)

---

## References

[1] Bergmann et al. "MVTec AD -- A Comprehensive Real-World Dataset for Unsupervised Anomaly Detection." *CVPR*, 2019.

[2] Radford et al. "Learning Transferable Visual Models From Natural Language Supervision." *ICML*, 2021.

[3] Hu et al. "LoRA: Low-Rank Adaptation of Large Language Models." *ICLR*, 2022.

[4] Dosovitskiy et al. "An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale." *ICLR*, 2021.

[5] Jeong and Jo. "HeadCLIP: A Visual-Language Model for Head CT Report Generation." *IEEE Access*, 2026.

[6] Jiang et al. "CLIP-Anomaly: Leveraging CLIP for Zero-Shot Anomaly Detection." *IEEE TNNLS*, 2025.

[7] Dohi et al. "WinCLIP: Zero-/Few-Shot Anomaly Classification and Segmentation." *CVPR*, 2026.

[8] Zhu et al. "AnomalyGPT: Detecting Industrial Anomalies using Large Vision-Language Models." *AAAI*, 2026.

[9] Li et al. "MambaAD: Is Mamba Effective for Time Series Anomaly Detection?" *IEEE TIST*, 2026.

---

*This project was completed as part of MAAI901 coursework requirements.*
