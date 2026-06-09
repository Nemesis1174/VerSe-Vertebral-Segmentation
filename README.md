# VerSe Vertebral Segmentation — CNN vs Transformer Comparison

[![Paper](https://img.shields.io/badge/Paper-IEEE-blue)](paper/paper.pdf)
[![Python](https://img.shields.io/badge/Python-3.10+-green)](https://python.org)

> **Comparative Analysis of CNN and Transformer Architectures for Multi-Class Vertebral Segmentation in CT Imaging**
> Cristian Aragon Salazar · Christopher Oswaldo Marquez Reyes
> Universidad Panamericana, Mexico

---

## Overview

Systematic comparison of three deep learning architectures on the **VerSe 2019+2020** benchmark (374 CT volumes, 28 vertebral labels C1-S1).

| Model | Architecture | Params (M) | DSC | ID Rate | VRAM (GB) | Total Train (h) |
|---|---|---|---|---|---|---|
| nnUNet | PlainConvUNet | 60.59 | 0.833 | 88.4% | 9.91 | 17.85 |
| **MedNeXt** | Large-kernel ConvNeXt | 31.66 | **0.854** | **91.5%** | 25.65 | 37.95 |
| SwinUNETR | Swin Transformer | 63.13 | 0.758 | 79.3% | 20.55 | 80.95 |

---

## Repository Structure

    VerSe-Vertebral-Segmentation/
    notebooks/
        01_preprocessing/
        02_training/
        03_inference/
        04_evaluation/
        05_reconstruction/
        06_paper_figures/
    figures/
        3d/
        ct_segmentation/
        metrics/
    results/
    paper/
    requirements.txt
    README.md

---

## Results

### Voxel-level Metrics (113 test cases)

| Model | DSC | ID Rate | RMSD (mm) |
|---|---|---|---|
| nnUNet | 0.833 | 0.884 | 2.96 |
| **MedNeXt** | **0.854** | **0.915** | **2.63** |
| SwinUNETR | 0.758 | 0.793 | 4.30 |

### Geometric Surface Metrics (10 test cases)

| Model | ASSD (mm) | Chamfer (mm) | HD95 (mm) | Hausdorff (mm) | Vol. Error (%) |
|---|---|---|---|---|---|
| nnUNet | **2.17** | 2.48 | **5.22** | 27.10 | 3.94 |
| **MedNeXt** | 2.20 | **2.37** | 5.44 | **25.03** | **3.66** |
| SwinUNETR | 2.30 | 2.61 | 5.64 | 50.92 | 6.41 |

### Computational Cost (NVIDIA RTX 3090 24GB)

| Model | Params (M) | VRAM (GB) | Train/fold (h) | Total 5-fold (h) |
|---|---|---|---|---|
| nnUNet | 60.59 | 9.91 | 3.57 | 17.85 |
| MedNeXt | 31.66 | 25.65 | 7.59 | 37.95 |
| SwinUNETR | 63.13 | 20.55 | 16.19 | 80.95 |

---

## Installation

    git clone https://github.com/Nemesis1174/VerSe-Vertebral-Segmentation.git
    cd VerSe-Vertebral-Segmentation
    pip install -r requirements.txt

---

## Reproduction Pipeline

1. **Dataset:** Download VerSe 2019+2020 from https://github.com/anjany/verse
2. **Preprocessing:** `notebooks/01_preprocessing/VerSe_Preprocessing.ipynb`
3. **Training:** `notebooks/02_training/`
4. **Inference:** `notebooks/03_inference/`
5. **Evaluation:** `notebooks/04_evaluation/Verse_Benchmark.ipynb`
6. **3D Reconstruction:** `notebooks/05_reconstruction/3D_MeshReconstruction_v3.ipynb`
7. **Paper Figures:** `notebooks/06_paper_figures/computational_cost.ipynb`

---

## Hardware Requirements

- **GPU:** NVIDIA RTX 3090 (24GB VRAM) or equivalent
- **RAM:** 32GB recommended
- **Storage:** ~120GB for full dataset

---

## Citation

    @inproceedings{aragon2025verse,
      title  = {Comparative Analysis of CNN and Transformer Architectures},
      author = {Aragon Salazar, Cristian and Marquez Reyes, Christopher},
      year   = {2025}
    }

---

## References

- Isensee et al., nnU-Net, Nature Methods 2021
- Roy et al., MedNeXt, MICCAI 2023
- Hatamizadeh et al., SwinUNETR, MICCAI 2021
- Sekuboyina et al., VerSe, Medical Image Analysis 2021
