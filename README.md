# Radar Signal Simulation and ML-Based Detection using SDR

## Overview
This project implements an end-to-end radar signal processing and machine learning pipeline for detecting Doppler radar returns in noisy environments. The system simulates atmospheric radar signals, performs classical signal processing techniques such as FFT-based Doppler estimation, and uses a Convolutional Neural Network (CNN) to classify radar signals from noise and clutter. The project is further extended to Software Defined Radio (SDR) using GNU Radio for real-time signal generation and data acquisition.

## Features
- Simulation of Doppler radar return signals
- Atmospheric noise and clutter modeling
- FFT-based Doppler frequency estimation
- Spectrogram generation for time-frequency analysis
- CNN-based signal vs noise classification
- Comparison with classical energy-based detection
- SDR implementation using GNU Radio
- Processing of real-time SDR-generated data

## System Architecture

```text
Radar Signal Generation
          ↓
Noise and Clutter Addition
          ↓
      FFT Analysis
          ↓
 Doppler Estimation
          ↓
 Spectrogram Generation
          ↓
      CNN Classifier
          ↓
 Signal / Noise Decision
```

For SDR implementation:

```text
GNU Radio Signal Source
          ↓
     Noise Source
          ↓
        Adder
          ↓
      File Sink
          ↓
     Python Pipeline
          ↓
 Spectrogram + CNN
```

## Methodology

### 1. Radar Signal Simulation
A Doppler radar signal is modeled as:

\[
f_d = \frac{2v}{\lambda}
\]

where:

- \(f_d\) = Doppler frequency
- \(v\) = target velocity
- \(\lambda\) = wavelength

The received baseband signal is generated and corrupted with additive Gaussian noise.

### 2. Signal Processing
- Fast Fourier Transform (FFT)
- Doppler peak estimation
- Velocity estimation from Doppler shift

### 3. Dataset Generation
Spectrograms are generated from:
- Signal + Noise samples
- Noise-only samples

The spectrogram images form the dataset for CNN training.

### 4. Machine Learning
A lightweight CNN is trained to classify:

- Class 0 → Noise Only
- Class 1 → Signal Present

## Experimental Results

### CNN Performance
- Test Accuracy: **90%**

Confusion Matrix:

```text
[[94   2]
 [18  86]]
```

- True Negatives: 94
- False Positives: 2
- False Negatives: 18
- True Positives: 86

### Classical Energy Detector
- Accuracy: **51.5%**

### Observation
The CNN significantly outperforms traditional energy-based detection methods, particularly in noisy environments and low-SNR conditions.

## Technologies Used

- Python
- NumPy
- SciPy
- Matplotlib
- PyTorch
- Scikit-Learn
- GNU Radio
- Jupyter Notebook


## Future Work
- Real-time SDR classification
- Range-Doppler map generation
- CFAR-based detection methods
- Multi-class velocity estimation
- Recurrent neural networks for temporal modeling
- Integration with real radar datasets

## Applications
- Wind Profiler Radar
- Atmospheric Sensing
- Weather Monitoring
- Radar Signal Intelligence
- Wireless Signal Detection
- SDR-based Radar Research

