# Supervised and Unsupervised Models for Fraud Detection

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Sklearn](https://img.shields.io/badge/Library-Scikit_Learn-orange)
![TensorFlow](https://img.shields.io/badge/Library-TensorFlow-orange)

## 📌 Overview

This project explores and compares the performance of **Supervised** and **Unsupervised** Machine Learning models in detecting credit card fraud. Given the highly imbalanced nature of financial transaction data, the study focuses on identifying efficient approaches to detect fraudulent activities while minimizing false positives and false negatives.

This work was developed as part of the **Data Mining and Machine Learning** course at **UNESP - Rio Claro** (Bachelor's in Computer Science).

## 🎯 Objectives

* **Compare Approaches:** Evaluate Supervised (Decision Tree, SVM) vs. Unsupervised (Isolation Forest, Autoencoders) models.
* **Handle Imbalance:** Analyze performance on a dataset where frauds represent only 0.172% of transactions.
* **Hybrid Solutions:** Explore combinations of models to optimize Precision and Recall.

## 📂 Dataset

The dataset used is the **Credit Card Fraud Detection** dataset available on Kaggle.

* **Instances:** 284,807 transactions.
* **Features:** 31 columns.
    * `V1` to `V28`: Principal components obtained via PCA (for confidentiality).
    * `Time`: Seconds elapsed between transactions.
    * `Amount`: Transaction value.
    * `Class`: Target variable (0 = Normal, 1 = Fraud).

## ⚙️ Methodology & Preprocessing

1.  **Data Integrity:** Confirmed no null or missing values were present.
2.  **Scaling:** Applied `StandardScaler` to `Amount` and `Time` features to normalize their range against the PCA components.
3.  **Outlier Analysis:** Verified the anomalous nature of fraud to justify the use of Anomaly Detection models.
4.  **Data Split:** Stratified split (75% test) to maintain fraud proportion.

## 🧠 Models Implemented

### Supervised
* **Decision Tree:** A balanced classifier for classification and regression.
* **SVM (Support Vector Machine):** Used for classification and outlier detection.

### Unsupervised (Anomaly Detection)
* **Isolation Forest:** Detects outliers by isolating observations.
* **Autoencoders:** Neural networks trained to compress and reconstruct normal data; high reconstruction error indicates potential fraud.

## 📊 Results

The models were evaluated based on Recall (Sensitivity), Precision, F1-Score, and AUC-ROC.

| Model | Recall | Precision | F1-Score | AUC | Note |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Decision Tree** | **0.76** | **0.83** | **0.79** | 0.88 | **Most Balanced Model** |
| **Autoencoder** | **0.83** | 0.13 | 0.22 | **0.96** | **Best Recall (Fraud Detection)** |
| **Isolation Forest**| 0.75 | 0.06 | 0.12 | 0.76 | Low Precision |
| **SVM** | 0.52 | 0.30 | 0.38 | 0.76 | Lowest Recall |

### Hybrid Solutions
Two hybrid strategies were tested to improve performance:

1.  **Reducing False Positives (Autoencoder + Decision Tree):**
    * Using Decision Tree to filter the Autoencoder's results.
    * **Result:** Precision improved to **0.85**, but Recall dropped to 0.73.
2.  **Reducing False Negatives:**
    * Combining models to catch more frauds.
    * **Result:** Performance was inferior (Recall 0.69), making this approach less advantageous.

## 📝 Conclusion

* **For High Recall:** The **Autoencoder** is the best choice if the priority is to catch as many frauds as possible, accepting a higher rate of false alarms.
* **For Balance:** The **Decision Tree** offers the best trade-off between Precision and Recall.
* **For High Precision:** A **Hybrid Solution** (Autoencoder filtered by Decision Tree) is ideal if minimizing false alarms is critical.

## 👥 Authors

* **Felipe Silva Alves de Oliveira**
* **Gabriella Alves de Oliveira**

---
*University Project - 2025*
