# ECG-RNN-Denoising-R-Peak-Detection-with-LSTM-GRU
Deep learning pipeline for ECG denoising and R-peak detection using LSTM and GRU models.

This repository contains an implementation of recurrent neural networks (RNNs) for **processing ECG signals**.  
The task is based on designing models to **denoise ECG data** and then **detect R-peaks** in the signals, following the assignment specifications.  

We use **LSTM** for denoising and **GRU** for R-peak detection, with added Gaussian noise augmentation and temporal segmentation.

---

## 📖 Problem Statement

ECG signals are inherently noisy. The goals of this project are:

1. **Denoising ECG signals** by designing an LSTM model to map noisy ECG segments to clean ones.  
2. **Detecting R-peaks** in ECG windows using a GRU classifier, labeling windows as containing an R-peak or not.  
3. **Evaluating performance** with error metrics (MAE, RMSE) for denoising, and classification metrics (Accuracy, Precision, Recall, F1) for R-peak detection.  
4. **Visualizing results** with plots of denoised signals, loss curves, and confusion matrices.

---

## 📂 Dataset

We assume access to an ECG dataset (e.g., MIT-BIH Arrhythmia Database).  

- Signals are preprocessed into windows of fixed size.  
- Gaussian noise with `σ = 0.05` is added to create noisy versions.  
- Each window is labeled as **containing an R-peak** or **not**.  

Data folder structure:
data/
raw/ # original ECG files
processed/ # augmented and windowed signals


---

## 🧰 Methodology

### **(a) Preprocessing**
- Segment ECG signals into fixed-size time windows.  
- Augment signals with Gaussian noise (σ = 0.05).  
- Store augmented signals in `data/processed/`.  

### **(b) LSTM Model for Denoising**
- Input: noisy ECG windows  
- Output: clean ECG windows  
- Architecture: stacked LSTM layers (up to 3), optimized for MSE loss  
- Metrics: **MAE** and **RMSE**  

### **(c) GRU Model for R-Peak Detection**
- Input: ECG segments (noisy or denoised)  
- Output: binary label (R-peak present / absent)  
- Architecture: GRU-based classifier with fully connected output  
- Metrics: **Accuracy, Precision, Recall, F1 Score**  

### **(d) Evaluation & Visualization**
- Loss curves for training and validation  
- Signal denoising comparison (noisy vs. clean vs. predicted)  
- Confusion matrix for classification results  
- CSV export with added column `R_peak`  

---

## 📊 Results

<img width="2479" height="1636" alt="image" src="https://github.com/user-attachments/assets/4ab6c7f7-dd94-4d7c-a322-bbeb2a75ac3b" />

---

## 📂 Repository Structure



ecg-rnn-denoise-rpeak/
├── Q2-Code.ipynb # Main notebook (LSTM + GRU models)
├── README.md # Documentation
├── requirements.txt # Dependencies
├── data/
│ ├── raw/ # Original ECG signals
│ └── processed/ # Augmented/segmented ECG signals
└── outputs/
├── csv/ # CSV files with predictions
├── plots/ # Training curves, ECG plots
└── models/ # Saved model checkpoints

