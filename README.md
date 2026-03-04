# EAL-Fusion

### Explainable Adaptive Layer for RGB–Depth–Thermal Person Segmentation

This repository contains the research work for **EAL-Fusion**, a multimodal deep learning framework for **person segmentation using RGB, Depth, and Thermal images**.

The model introduces an **Explainable Adaptive Layer (EAL)** that dynamically learns **per-pixel modality weights**, improving segmentation robustness in difficult environments such as low light and occlusion.

---

## Authors

Havva Zimra
Ayshath Sahada
Rameeza Hazara
Ms Nausheeda BS

PG Department of SIST
AIMIT – St Aloysius (Deemed to be University)
Mangaluru, India

---

# Project Overview

Traditional RGB-based segmentation models often fail under:

• low lighting
• shadows
• occlusion

To overcome these challenges, this project integrates three sensing modalities:

* RGB images
* Depth maps
* Thermal images

The Explainable Adaptive Layer dynamically determines which modality is most reliable for each pixel.

---

# Dataset

The model was trained and evaluated on the **TriStar Multimodal People Segmentation Dataset**.

| Split      | Samples |
| ---------- | ------- |
| Training   | 2000    |
| Validation | 500     |
| Testing    | 300     |

All images were resized to **256×256 resolution**.

---

# Results

| Metric    | Score  |
| --------- | ------ |
| IoU       | 0.4423 |
| Dice      | 0.5506 |
| Precision | 0.6811 |
| Recall    | 0.5432 |
| Accuracy  | 0.9759 |

---

# Research Paper

The full research paper is available in the **paper** folder of this repository.

---

# Implementation

The model was implemented using **PyTorch** with CUDA GPU acceleration.

---

# Future Work

Future improvements include:

• multi-object segmentation
• real-time deployment
• transformer-based multimodal fusion

---

# License

MIT License
