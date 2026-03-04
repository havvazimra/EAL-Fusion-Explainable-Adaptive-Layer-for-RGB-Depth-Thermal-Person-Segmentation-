# EAL-Fusion

### Explainable Adaptive Layer for RGB–Depth–Thermal Person Segmentation

EAL-Fusion is a deep learning framework designed for **robust human segmentation using multimodal sensor data**. The model integrates **RGB, Depth, and Thermal modalities** and introduces an **Explainable Adaptive Layer (EAL)** that dynamically determines which modality should be trusted for each pixel.

This approach improves segmentation reliability in **challenging environments such as low illumination, shadows, and occlusion**.

---

# Authors

Havva Zimra,
Ayshath Sahada,
Rameeza Hazara,
Ms Nausheeda BS

PG Department of SIST
AIMIT – St Aloysius (Deemed to be University)
Mangaluru, India

---

# Abstract

Image segmentation plays a crucial role in computer vision applications such as surveillance systems, robotics, and autonomous navigation. Traditional RGB-based segmentation models often fail under difficult environmental conditions.

EAL-Fusion addresses this limitation by combining **RGB appearance information, Depth spatial geometry, and Thermal heat signatures**. The model dynamically assigns **per-pixel modality confidence weights**, enabling adaptive fusion of multimodal features.

The Explainable Adaptive Layer produces **confidence maps** that reveal which sensor contributed most to each segmentation decision.

---

## Workflow Overview

<img width="496" height="1470" alt="image" src="https://github.com/user-attachments/assets/e256eff2-60fc-4b22-b8f9-49267fe143a3" />


---

# Key Contributions

• Multimodal fusion using **RGB, Depth, and Thermal sensors**
• Pixel-wise **adaptive modality weighting**
• Interpretable **modality confidence maps**
• Robust person segmentation in low-light environments
• Lightweight deep learning architecture implemented in **PyTorch**

---

# Model Architecture

The EAL-Fusion architecture consists of:

1. RGB Encoder
2. Depth Encoder
3. Thermal Encoder
4. Explainable Adaptive Layer (EAL)
5. Multimodal Feature Fusion
6. Segmentation Decoder

The EAL layer computes modality weights using a softmax function:

αr, αd, αt = Softmax(frgb, fdepth, fthermal)

Where:

• αr – RGB confidence
• αd – Depth confidence
• αt – Thermal confidence

The fused feature representation is:

Ffused = αrFrgb + αdFdepth + αtFthermal

---

# Dataset

Experiments were conducted using the **TriStar Multimodal People Segmentation Dataset**.

| Dataset Split | Samples |
| ------------- | ------- |
| Training      | 2000    |
| Validation    | 500     |
| Testing       | 300     |

Each sample includes:

• RGB image
• Depth map
• Thermal image
• Binary person segmentation mask

All images were resized to **256 × 256 pixels**.

---

# Training Setup

| Parameter     | Value                     |
| ------------- | ------------------------- |
| Framework     | PyTorch 2.0               |
| Optimizer     | Adam                      |
| Learning Rate | 1×10⁻⁴                    |
| Batch Size    | 6                         |
| Epochs        | 18                        |
| Hardware      | NVIDIA GPU (CUDA enabled) |

---

# Results

| Metric    | Score  |
| --------- | ------ |
| IoU       | 0.4423 |
| Dice      | 0.5506 |
| Precision | 0.6811 |
| Recall    | 0.5432 |
| Accuracy  | 0.9759 |

The results demonstrate improved segmentation robustness compared to single-modality approaches.

---
## Qualitative Segmentation Results

<img width="597" height="1024" alt="image" src="https://github.com/user-attachments/assets/1f78518d-27d6-4ea8-ad1a-1c353ac62867" />

---

# Explainability

The Explainable Adaptive Layer produces **modality confidence maps** that visualize which sensor contributed most to each pixel's prediction.

Typical observations:

• RGB dominates under good lighting conditions
• Depth improves object boundaries and geometry
• Thermal ensures detection in low-light environments

---

# Future Work

• Multi-object segmentation
• Transformer-based multimodal fusion
• Real-time embedded deployment
• Sensor reliability and uncertainty estimation

---

# Acknowledgment

The authors express gratitude to the faculty of the **PG Department of SIST, AIMIT, St Aloysius (Deemed to be University), Mangaluru**, for their guidance and support throughout this research.

---

# License

MIT License
