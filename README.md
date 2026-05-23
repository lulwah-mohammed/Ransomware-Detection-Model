# Machine Learning Approaches for Ransomware Detection in IoT Environments

An advanced, multi-perspective Intrusion Detection System (IDS) designed specifically for resource-constrained Internet of Things (IoT) environments. This project explores and evaluates Network-based, Host-based, and Hybrid machine learning frameworks to achieve early and highly accurate ransomware detection.

---

## Project Overview
The rapid expansion of IoT devices in critical sectors has exponentially increased the risk of devastating cyberattacks, particularly ransomware. Due to limited computational resources and weak firmware security, traditional signature-based security mechanisms often fall short.

This project addresses these gaps by implementing and evaluating five distinct Machine Learning (ML) algorithms under three architectural approaches, leveraging the realistic ToN-IoT dataset.

### Key Contributions
* Three-Way Detection Architecture: Developed standalone Host-based, Network-based, and combined Hybrid detection pipelines.
* Feature-Level Fusion: Demonstrated that combining raw host and network feature spaces significantly optimizes the model's capacity to spot complex ransomware behavior.
* Ensemble Learning Mastery: Showcased the superior capabilities of ensemble techniques against traditional linear baselines in handling highly imbalanced, real-world workloads.

---

## Detection Approaches

1. Network-Based Approach: Focuses on high-level communication patterns and metadata flow connection activity (13 selected low-cardinality features) without requiring heavy payload decryption or deep packet inspection.
2. Host-Based Approach: Monitors internal device telemetry, including process behavior, file activity (creation, modification, deletion), and memory footprints to spot early encryption attempts.
3. Hybrid Approach: Integrates both domains. Features are aligned, combined via column-wise feature concatenation, and used to retrain classifiers for multi-source holistic visibility.

---

## Evaluated Models & Configurations

All models were developed in Python 3.13.9 utilizing standard libraries (scikit-learn, XGBoost, CatBoost). To ensure reproducibility, a random_state=42 was strictly maintained across evaluations.

* Random Forest (RF): n_estimators=100
* XGBoost: n_estimators=100, max_depth=6, learning_rate=0.1
* CatBoost: iterations=100, depth=6, learning_rate=0.1
* K-Nearest Neighbors (KNN): n_neighbors=5
* Logistic Regression (LR): max_iter=1000

---

## Key Results & Performance Outcomes

While training was strictly balanced (1:1 ratio) via random undersampling, the testing phase utilized an intentionally imbalanced distribution (91.6% Normal vs. 8.4% Ransomware) to mirror real-world environments realistically.

### Performance Summary Table (Class 1: Malicious)

| Detection Approach | Best Performing Models | Precision | Recall | F1-Score | Overall Accuracy |
| :--- | :--- | :---: | :---: | :---: | :---: |
| Host-Based | XGBoost / CatBoost | 0.78 / 0.76 | 0.87 / 0.92 | **0.83** | 0.82 / 0.81 |
| Network-Based | RF / XGBoost / CatBoost | ~0.99 | 1.00 | **0.99** | **1.00** |
| Hybrid (Feature-Level) | XGBoost / CatBoost | **1.00** | **1.00** | **1.00** | **1.00** |

> Note: Feature-level fusion using XGBoost and CatBoost achieved perfect classification metrics (F1 = 1.00), representing an absolute improvement of 0.18 points over decision-level OR-fusion, and outperforming standalone host-based models by 0.17 points. Linear models (LR) struggled drastically under real-world imbalanced data, yielding high numbers of false positives.

---

## Repository Structure & Dataset Access

### Dataset Link
The models are evaluated using the standard ToN-IoT Dataset. Due to file size constraints, the raw data files are not hosted in this repository. You can download the official subsets directly from:
[Official ToN-IoT Dataset Repository (IEEE DataPort)](https://ieee-dataport.org/documents/toniot-datasets)

### File Structure
```text
├── Host.ipynb              # Host-based Ransomware Detection pipeline
├── Network.ipynb           # Network-based Ransomware Detection pipeline
├── Hybrid.ipynb            # Hybrid Feature-level Fusion pipeline
├── ProjectReport.pdf       # Graduation Project Final Report
└── README.md               # Main repository roadmap
```
---

## Authors & Team
Developed with passion by the Computer Science Department at **Imam Mohammad Ibn Saud Islamic University** (College of Computer and Information Sciences):

* **Lulwah Mohammed Alhabdan**
* **Elaf Ibrahim Aljurayed**
* **Ethar Ibrahim Aljurayed**
* **Lamees Ayadh Alafari**

**Supervisor:** Dr. Tahani Albalawi
