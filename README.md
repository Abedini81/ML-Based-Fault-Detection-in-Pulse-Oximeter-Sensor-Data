# ML-Based Fault Detection in Pulse Oximeter Sensor Data

This repository contains a Python implementation of an **unsupervised machine learning pipeline** for detecting faults in **pulse oximeter sensor data**.  
The approach uses **preprocessing, feature extraction, normalization across recordings, and anomaly detection** to flag unusual sensor behaviors.  

⚠️ **Note**: This is an **educational project**, not a clinical diagnostic tool.

---

## Overview

Pulse oximeters measure **oxygen saturation (SpO₂)** and **heart rate (HR)**. These devices are widely used in both clinical and home-care settings.  
However, faulty readings due to **motion artifacts, poor sensor contact, or environmental interference** can cause **false alarms** or **missed emergencies**.  

This project demonstrates a **machine learning-based workflow** for detecting faulty readings:

1. Load and preprocess real-world physiological data.  
2. Handle missing values and physiologically implausible measurements.  
3. Extract statistical, dynamic, and data-quality features.  
4. Normalize features across all recordings.  
5. Apply **Isolation Forest** for unsupervised anomaly detection.  
6. Provide an outline of evaluation metrics (precision, recall, F1).  

---

## Dataset

I used the **[BIDMC PPG and Respiration Dataset (PhysioNet)](https://physionet.org/content/bidmc/1.0.0/)**.  

- **Subjects:** 53 ICU patients  
- **Signals (125 Hz):** PPG, impedance respiration, ECG  
- **Parameters (1 Hz):** SpO₂, HR, respiratory rate  

**Focus in this project:**  
- SpO₂ (oxygen saturation, %)  
- HR (heart rate, bpm)  

---

## Preprocessing

Steps implemented in the notebook:

- **Missing value handling** → Drop NaNs.  
- **Implausible values** → Remove SpO₂ < 50% or > 100%, HR < 20 bpm or > 220 bpm.  
- **Feature extraction** →  
  - Statistical: mean, variance  
  - Dynamic: maximum jump (sudden change), stuck value count  
- **Normalization** → Features are normalized **across all recordings** so they are on a comparable scale before anomaly detection.  

---

## Algorithm

The core ML model is an **Isolation Forest**:

- Type: Unsupervised anomaly detection  
- Goal: Learn "normal" sensor behavior and flag deviations as potential faults  
- Advantage: Works without labeled data (important for medical datasets where faults are rarely annotated)  

➡️ *[Placeholder: Insert pseudocode or pipeline diagram]*  

---

## 📈 Evaluation

The dataset does **not contain ground-truth fault labels**, so:

- Precision/Recall/F1 metrics are included for illustration only.  
- In practice, evaluation requires either:
  - Expert-annotated fault labels, or  
  - Synthetic fault injection for benchmarking.  

➡️ *[Placeholder: Add results, charts, or anomaly detection visualizations]*  


## Note

This project is for educational and research purposes only.
It is not intended for clinical decision-making.
