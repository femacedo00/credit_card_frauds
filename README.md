# Supervised and Unsupervised Models for Fraud Detection

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Sklearn](https://img.shields.io/badge/Library-Scikit_Learn-orange)
![TensorFlow](https://img.shields.io/badge/Library-TensorFlow-orange)

## 📌 Overview

This project explores and compares the performance of **Supervised** and **Unsupervised** Machine Learning models in detecting credit card fraud. [cite_start]Given the highly imbalanced nature of financial transaction data, the study focuses on identifying efficient approaches to detect fraudulent activities while minimizing false positives and false negatives[cite: 30, 31, 35].

[cite_start]This work was developed as part of the **Data Mining and Machine Learning** course at **UNESP - Rio Claro** (Bachelor's in Computer Science)[cite: 3, 205].

## 🎯 Objectives

* [cite_start]**Compare Approaches:** Evaluate Supervised (Decision Tree, SVM) vs. Unsupervised (Isolation Forest, Autoencoders) models[cite: 38, 39].
* [cite_start]**Handle Imbalance:** Analyze performance on a dataset where frauds represent only 0.172% of transactions[cite: 49].
* [cite_start]**Hybrid Solutions:** Explore combinations of models to optimize Precision and Recall[cite: 41].

## 📂 Dataset

[cite_start]The dataset used is the **Credit Card Fraud Detection** dataset available on Kaggle[cite: 46].

* **Instances:** 284,807 transactions.
* **Features:** 31 columns.
    * [cite_start]`V1` to `V28`: Principal components obtained via PCA (for confidentiality)[cite: 50, 54].
    * [cite_start]`Time`: Seconds elapsed between transactions[cite: 55].
    * [cite_start]`Amount`: Transaction value[cite: 55].
    * [cite_start]`Class`: Target variable (0 = Normal, 1 = Fraud)[cite: 56].

## ⚙️ Methodology & Preprocessing

1.  [cite_start]**Data Integrity:** Confirmed no null or missing values were present[cite: 62, 63].
2.  [cite_start]**Scaling:** Applied `StandardScaler` to `Amount` and `Time` features to normalize their range against the PCA components[cite: 76, 80].
3.  [cite_start]**Outlier Analysis:** Verified the anomalous nature of fraud to justify the use of Anomaly Detection models[cite: 85].
4.  [cite_start]**Data Split:** Stratified split (75% test) to maintain fraud proportion[cite: 123].

## 🧠 Models Implemented

### Supervised
* [cite_start]**Decision Tree:** A balanced classifier for classification and regression[cite: 132].
* [cite_start]**SVM (Support Vector Machine):** Used for classification and outlier detection[cite: 133].

### Unsupervised (Anomaly Detection)
* [cite_start]**Isolation Forest:** Detects outliers by isolating observations[cite: 135].
* [cite_start]**Autoencoders:** Neural networks trained to compress and reconstruct normal data; high reconstruction error indicates potential fraud[cite: 138, 147].

## 📊 Results

The models were evaluated based on Recall (Sensitivity), Precision, F1-Score, and AUC-ROC.

| Model | Recall | Precision | F1-Score | AUC | Note |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Decision Tree** | **0.76** | **0.83** | **0.79** | 0.88 | [cite_start]**Most Balanced Model** [cite: 172, 182] |
| **Autoencoder** | **0.83** | 0.13 | 0.22 | **0.96** | [cite_start]**Best Recall (Fraud Detection)** [cite: 178, 183] |
| **Isolation Forest**| 0.75 | 0.06 | 0.12 | 0.76 | [cite_start]Low Precision [cite: 176] |
| **SVM** | 0.52 | 0.30 | 0.38 | 0.76 | [cite_start]Lowest Recall [cite: 174] |

### Hybrid Solutions
Two hybrid strategies were tested to improve performance:

1.  **Reducing False Positives (Autoencoder + Decision Tree):**
    * Using Decision Tree to filter the Autoencoder's results.
    * [cite_start]**Result:** Precision improved to **0.85**, but Recall dropped to 0.73[cite: 190].
2.  **Reducing False Negatives:**
    * Combining models to catch more frauds.
    * [cite_start]**Result:** Performance was inferior (Recall 0.69), making this approach less advantageous[cite: 188, 195].

## 📝 Conclusion

* [cite_start]**For High Recall:** The **Autoencoder** is the best choice if the priority is to catch as many frauds as possible, accepting a higher rate of false alarms[cite: 200].
* [cite_start]**For Balance:** The **Decision Tree** offers the best trade-off between Precision and Recall[cite: 201].
* [cite_start]**For High Precision:** A **Hybrid Solution** (Autoencoder filtered by Decision Tree) is ideal if minimizing false alarms is critical[cite: 202].

## 👥 Authors

* **Felipe Silva Alves de Oliveira**
* **Gabriella Alves de Oliveira**

---
*University Project - 2025*
