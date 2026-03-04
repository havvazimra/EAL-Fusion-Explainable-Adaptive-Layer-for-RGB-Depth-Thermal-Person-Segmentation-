# EAL-Fusion

### Explainable Adaptive Layer for RGB–Depth–Thermal Person Segmentation

EAL-Fusion is a multimodal deep learning framework designed for **robust human segmentation** using **RGB, Depth, and Thermal sensor data**. The model introduces an **Explainable Adaptive Layer (EAL)** that dynamically learns **per-pixel modality importance**, enabling accurate segmentation even in challenging conditions such as **low light, shadows, and occlusion**.

---

## Authors

Havva Zimra,
Ayshath Sahada,
Rameeza Hazara,
Ms Nausheeda BS

PG Department of SIST
AIMIT – St Aloysius (Deemed to be University)
Mangaluru, India

---

# Abstract

Image segmentation plays a key role in computer vision applications such as surveillance systems, robotics, and autonomous navigation. However, traditional RGB-based segmentation methods often struggle in complex environments with poor illumination or occlusions.

This project proposes **EAL-Fusion**, an explainable multimodal fusion architecture for **RGB–Depth–Thermal (RDT) segmentation**. The model dynamically weights each modality at a **pixel level**, producing interpretable **confidence maps** that reveal which sensor contributes most during segmentation.

The model was implemented using **PyTorch** and evaluated on the **TriStar Multimodal People Segmentation Dataset**.

### Performance Results

| Metric    | Score  |
| --------- | ------ |
| IoU       | 0.4423 |
| Dice      | 0.5506 |
| Precision | 0.6811 |
| Recall    | 0.5432 |
| Accuracy  | 0.9759 |

The model focuses specifically on **person segmentation**, demonstrating strong robustness in low-visibility environments.

---

# Motivation

Standard RGB segmentation systems fail in conditions such as:

• low lighting
• shadows
• occlusion
• nighttime environments

To overcome these limitations, **multimodal fusion** integrates information from multiple sensors:

| Modality | Information Provided           |
| -------- | ------------------------------ |
| RGB      | Appearance and color           |
| Depth    | Spatial structure and geometry |
| Thermal  | Heat signatures of humans      |

EAL-Fusion allows the model to **adaptively decide which modality to trust for each pixel**.

---

# Methodology

The EAL-Fusion architecture consists of three main stages:

### 1. Multimodal Feature Extraction

Separate encoder networks process:

• RGB images
• Depth maps
• Thermal images

Each encoder extracts spatial features from its respective modality.

---

### 2. Explainable Adaptive Layer (EAL)

The core innovation of this work is the **Explainable Adaptive Layer**, which estimates **per-pixel modality confidence weights**.

The modality weights are computed using a **Softmax function**:

αr, αd, αt = Softmax(frgb, fdepth, fthermal)

Where:

• αr — RGB confidence weight
• αd — Depth confidence weight
• αt — Thermal confidence weight

The weights satisfy:

αr + αd + αt = 1

---

### 3. Multimodal Fusion

The final fused feature representation is calculated as:

Ffused = αrFrgb + αdFdepth + αtFthermal

This enables the model to dynamically combine sensor information depending on the environment.

---

# Loss Function

Training uses a combination of **Binary Cross-Entropy Loss** and **Dice Loss**:

Ltotal = LBCE + 0.5 × LDice

Where:

• BCE penalizes incorrect pixel classifications
• Dice loss improves segmentation overlap accuracy

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
• Binary person mask

All images were resized to **256 × 256 resolution**.

---

# Training Setup

| Parameter     | Value             |
| ------------- | ----------------- |
| Framework     | PyTorch 2.0       |
| Optimizer     | Adam              |
| Learning Rate | 1×10⁻⁴            |
| Batch Size    | 6                 |
| Epochs        | 18                |
| Hardware      | NVIDIA GPU (CUDA) |

---

# Explainability

The Explainable Adaptive Layer generates **modality confidence maps** that visualize which sensor contributed most during segmentation.

Typical behavior:

• RGB dominates in well-lit environments
• Depth improves object boundaries
• Thermal detects humans in darkness

These visualizations improve **model interpretability and trustworthiness**.

---

# Future Work

Possible future extensions include:

• multi-object segmentation
• real-time deployment on embedded systems
• transformer-based multimodal fusion
• uncertainty estimation for modality reliability

---

# Acknowledgment

The authors thank the faculty of the **PG Department of SIST, AIMIT, St Aloysius (Deemed to be University), Mangaluru** for their guidance and support throughout this research.

---

# License

This project is licensed under the **MIT License**.
