# Hybrid Audio-Visual Approach for Localizing 3D Active Speakers
This repository contains supplementary materials for the paper "A Hybrid Audio-Visual Approach for Localizing 3D Active Speakers". The study introduces a method to estimate the 3D Cartesian coordinates of two active speakers by integrating MediaPipe's Pose Estimation and Face Mesh with SALSA-Lite audio positioning using a 4-channel microphone array and a webcam.
# Supplements Overview

This section provides a brief overview of the four supplementary files associated with the research study. Each supplement is explained below with a link to the respective file for further reference.

## Supplement 1: Literature Review

This supplement presents a comparison of various methods for audio event localization using audio-visual information. The key approaches and the underlying scenarios are summarized in the table below:

| **Method** | **Scenario** | **Key Features** |
|------------|--------------|------------------|
| Audio | Static speakers | Uses audio for localization, often suffers from high track loss in dynamic environments. |
| Video | Static speakers | Relies on visual information for localization, limited by visibility and lighting. |
| Audio-Visual (AV) | Dynamic speakers | Combines audio and visual data for improved accuracy, reducing track loss and estimation errors. |

The table provides a high-level comparison of different localization methods and their performance under varying conditions.

## Supplement 2: Calibration Methodology

This supplement describes the calibration process used to convert 2D pixel coordinates to real-world coordinates using a neural network. The methodology includes the following key steps:

1. **Visual Scene Setup**: The scene is set up with a rectangular floor area covered with checkerboard plots. The camera is placed 320 cm away from the floor and aligned with the reference point.
2. **Dataset Generation**: A dataset is created by placing a 15cm × 15cm square at various points across the scene. The positions of the square are tracked for 3 seconds at each position.
3. **Neural Network Training**: A neural network is trained using the generated dataset. The network maps pixel coordinates to real-world coordinates. The architecture includes three hidden layers with 300, 32, and 16 neurons, and the network is optimized using the Adam optimizer.
4. **Model Performance**: The model is trained over 700 epochs, and the Mean Squared Error (MSE) is evaluated for both the training and evaluation sets, showing significant performance with an MSE of 1.50 for the evaluation set.

## Supplement 3: Audio Localization Performance

This supplement describes the assessment of the audio localization method using the TAU-NIGENS Spatial Sound Events datasets. The following key points are covered:

- **Datasets Used**: The TAU-NIGENS Spatial Sound Events 2021 and 2020 datasets are used to train and test the neural network for audio localization.
- **Recording Setup**: Audio is recorded using the ReSpeaker USB Mic Array, which has four channels. Multiple conditions are considered, including one or two speakers, movement, background noise, and different room environments.
- **Evaluation Metrics**: The performance of the trained network is evaluated using the Track Loss Rate (TLR) and Average Euclidean Distance (AED) between estimated positions and ground-truth values. The results show a significant improvement in localization accuracy when using audio-visual fusion.

## Supplement 4: Overall Performance Comparison

This supplement compares the overall performance of the Audio (A), Video (V), and Audio-Visual (AV) localization methods using two main metrics: Track Loss Rate (TLR) and Average Euclidean Distance (AED). The results are summarized in the tables below:

### Table 1: Track Loss Rate (TLR) of Audio (A), Video (V), and Audio-Visual (AV) Approaches

| **Duration (Frame No.)** | **100-150** | **151-200** | **201-300** | **400-450** | **451-500** | **501-600** |
|--------------------------|-------------|-------------|-------------|-------------|-------------|-------------|
| **Seq1**                 |             |             |             |             |             |             |
| A S1                     | 11.76       | –           | 9           | 50.98       | –           | 41          |
| V S1                     | 0           | –           | 36          | 5.88        | –           | 2           |
| AV                        | 0           | –           | 0           | 0           | –           | 0           |
| **Seq2**                 |             |             |             |             |             |             |
| A S1                     | 21          | –           | 40          | 23          | –           | 38          |
| V S1                     | 7.8         | –           | 18          | 0           | –           | 0           |
| AV                        | 0           | –           | 2           | 0           | –           | 0           |

### Table 2: Average Euclidean Distance (AED) of Audio (A), Video (V), and Audio-Visual (AV) Approaches

| **Duration (Frame No.)** | **100-150** | **151-200** | **201-300** | **400-450** | **451-500** | **501-600** |
|--------------------------|-------------|-------------|-------------|-------------|-------------|-------------|
| **Seq1**                 |             |             |             |             |             |             |
| A S1                     | 9.2         | –           | 11.1        | 8.86        | –           | 9.01        |
| V S1                     | 9.53        | –           | 9.05        | 8.58        | –           | 3.14        |
| AV                        | 2.34        | –           | 4.87        | 7.2         | –           | 3.9         |
| **Seq2**                 |             |             |             |             |             |             |
| A S1                     | 8.29        | –           | 10.8        | 8.5         | –           | 9.4         |
| V S1                     | 2.13        | –           | 2.38        | 3.72        | –           | 2.82        |
| AV                        | 3.37        | –           | 3.59        | 2.75        | –           | 2.48        |

### Key Findings:
- The AV method outperforms both the Audio and Video methods, with a significant reduction in Track Loss Rate (TLR) and Average Euclidean Distance (AED).
- In scenarios where multiple speakers are present, both TLR and AED increase, especially in the audio method.
- Head rotation and background light intensity affect the accuracy of localization, with significant changes in TLR observed during these conditions.

For more detailed results, please refer to the supplementary files on the [GitHub repository](https://github.com/esfehaniparisa/A-hybrid-audio-visual-approach-for-localizing-3D-active-speakers-/tree/main).

