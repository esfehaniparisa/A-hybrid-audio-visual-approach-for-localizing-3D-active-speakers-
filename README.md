
# Hybrid Audio-Visual Approach for Localizing 3D Active Speakers

[![DOI](https://zenodo.org/badge/DOI/DOI: 10.5281/zenodo.21813612.svg)](https://doi.org/DOI: 10.5281/zenodo.21813612)

This repository contains supplementary materials for the paper **"A Hybrid Audio-Visual Approach for Localizing 3D Active Speakers"**. The study introduces a method to estimate the 3D Cartesian coordinates of two active speakers by integrating MediaPipe's Pose Estimation and Face Mesh with SALSA-Lite audio positioning using a 4-channel microphone array and a webcam.

---

## Overview

🔹 **Audio Processing**: Uses a neural network with SALSA-Lite features to localize sound sources in azimuth and elevation.  
🔹 **Visual Processing**: Employs Pose Estimation and Face Mesh from MediaPipe for speaker localization.  
🔹 **Fusion Strategy**: Combines audio and visual estimations using a stacking-based ensemble learning approach.

---
### SALSA-Lite Audio Source Localization

The audio localization component used in this work is based on the publicly available SALSA-Lite framework developed by the original authors.

The SALSA-Lite source code was obtained from:

https://github.com/thomeou/SALSA-Lite

The original implementation was installed and integrated into our proposed audio-visual localization pipeline to extract audio localization features and estimate sound source directions.
---
## Key Findings

✅ The proposed method significantly reduces tracking loss from 35.58% (audio-only) to 3.36% (audio-visual fusion).  
✅ **Estimation Error**: 8.91 (audio-only) → 4.61 (visual) → 4.09 (combined audio-visual).  
✅ The approach improves robustness in noisy, reverberant, and dynamic environments.

---

## Future Work

🔹 Improving camera calibration for more accurate real-world coordinate transformation.  
🔹 Extending the framework to multiple simultaneous speakers.  
🔹 Enhancing audio localization using transfer learning.

---

# 📊 Dataset Description

The dataset used in this work is composed of synchronized multi-modal recordings.

---

## 1. Calibration Dataset (2D → 3D Mapping)

- Purpose: Learn mapping from image coordinates to real-world coordinates  
- Data type: Checkerboard-based spatial samples  
- Input: 2D pixel coordinates  
- Output: 3D Cartesian coordinates  
- Used for: Camera calibration and spatial transformation  
- Setup: Fixed camera (320 cm distance), grid-based sampling  

---

## 2. Audio Dataset

- Source: TAU-NIGENS Spatial Sound Events dataset (2020 & 2021)  
- Device: 4-channel ReSpeaker microphone array  
- Content:
  - Single speaker scenarios  
  - Multi-speaker scenarios  
  - Moving speakers  
  - Noisy and reverberant environments  
- Features: SALSA-Lite-based acoustic representations  

---

## 3. Visual Dataset

- Device: Monocular RGB camera  
- Framework: MediaPipe (Pose Estimation + Face Mesh)  
- Content:
  - Facial landmarks  
  - Body pose keypoints  
  - Temporal tracking of speakers  
- Conditions:
  - Lighting variation  
  - Occlusion  
  - Head motion  

---

## 4. Audio-Visual Fusion Dataset

- Input: Combined audio + visual features  
- Structure:
  - Audio localization outputs  
  - Visual localization outputs  
  - Ground truth 3D positions  
- Purpose: Training fusion network for final 3D estimation  

---

## Dataset Availability
  
To ensure reproducibility, a representative subset of the dataset is publicly available in this repository.

The complete dataset is large-scale and therefore not publicly released at this stage due to storage constraints.

A sample of the dataset can be accessed via Google Drive:

👉 [Access Sample Dataset](https://drive.google.com/drive/folders/1AZVfsJjmzGrRGS7pOixtK_MQhVqjC1gH?usp=drive_link)

The full dataset will be shared upon request after publication.

---

## Supplements Overview

---

### Supplement 1: Literature Review

| Method | Scenario | Key Features |
|--------|----------|--------------|
| Audio | Static speakers | High tracking loss in dynamic environments |
| Video | Static speakers | Sensitive to occlusion and lighting |
| Audio-Visual | Dynamic speakers | Improved accuracy via multimodal fusion |

---

### Supplement 2: Calibration Methodology

- Checkerboard floor setup  
- Camera at 320 cm distance  
- Dataset: 15cm × 15cm marker samples  
- Neural network: 300 → 32 → 16  
- Optimizer: Adam  
- MSE ≈ 1.50  

---

### Supplement 3: Audio Localization Performance

- Dataset: TAU-NIGENS 2020 & 2021  
- Microphone: 4-channel array  
- Scenarios: noise, motion, multi-speaker  

Metrics:
- Track Loss Rate (TLR)  
- Average Euclidean Distance (AED)  

---

### Supplement 4: Overall Performance Comparison

#### Table 1: Track Loss Rate (TLR)

| Duration | 100–150 | 151–200 | 201–300 | 400–450 | 451–500 | 501–600 |
|----------|--------|--------|--------|--------|--------|--------|
| A S1 Seq1 | 11.76 | – | 9 | 50.98 | – | 41 |
| V S1 Seq1 | 0 | – | 36 | 5.88 | – | 2 |
| AV Seq1 | 0 | – | 0 | 0 | – | 0 |
| A S1 Seq2 | 21 | – | 40 | 23 | – | 38 |
| V S1 Seq2 | 7.8 | – | 18 | 0 | – | 0 |
| AV Seq2 | 0 | – | 2 | 0 | – | 0 |

---

#### Table 2: Average Euclidean Distance (AED)

| Duration | 100–150 | 151–200 | 201–300 | 400–450 | 451–500 | 501–600 |
|----------|--------|--------|--------|--------|--------|--------|
| A S1 Seq1 | 9.2 | – | 11.1 | 8.86 | – | 9.01 |
| V S1 Seq1 | 9.53 | – | 9.05 | 8.58 | – | 3.14 |
| AV Seq1 | 2.34 | – | 4.87 | 7.2 | – | 3.9 |
| A S1 Seq2 | 8.29 | – | 10.8 | 8.5 | – | 9.4 |
| V S1 Seq2 | 2.13 | – | 2.38 | 3.72 | – | 2.82 |
| AV Seq2 | 3.37 | – | 3.59 | 2.75 | – | 2.48 |

---

### Key Observations

- Audio-Visual fusion consistently outperforms single modalities.  
- Multi-speaker scenarios increase difficulty for audio-only systems.  
- Environmental conditions significantly affect performance.

---
