
#  Predictive Analytics for Human Activity Recognition (HAR) with OxWearables SSL Models

**Author:** Abideep Kondal  
**Focus:** Analysis of Self-Supervised Learning (SSL) models for HAR using the OxWearables framework.

---

##  Project Overview

This repository presents an independent analysis and extension of the OxWearables self-supervised learning (SSL) models applied to Human Activity Recognition (HAR). The goal is to evaluate the performance of the HaRNet10 SSL model across multiple real-world datasets and demonstrate its effectiveness compared to traditional models like Random Forest.

---

##  Paper Summary: OxWearables SSL for HAR

###  Introduction

Human Activity Recognition (HAR) suffers from data labeling constraints. OxWearables proposes using SSL with three pretext tasks (Arrow of Time, Permutation, Time Warping) to train HAR models on large-scale unlabeled data from the UK-Biobank.

###  Dataset

- **UK Biobank**: 700k+ person-days of wrist-worn accelerometer data at 100Hz, resampled to 30Hz.
- Windowed into 10-second segments.
- Evaluated across 7 external datasets.

###  Model Architecture

- **Base**: ResNet-V2 (18-layer, 1D Conv)
- **SSL Tasks**: AoT, Permutation, TW
- **Optimization**: Adam, weighted sampling for dynamic segments

###  Evaluation

- Cross-validation by subject count (Held-one-out / 5-fold)
- SSL models fine-tuned on downstream tasks outperformed traditional models significantly (up to +55% F1 improvement on small datasets).

---

##  My Analysis: HaRNet10 SSL Model

###  ADL Dataset

- Preprocessed at 30Hz, 12 activity classes
- Model: HaRNet10 with adjusted classifier
- Results: F1 score improved from **0.79 → 0.97** in 10 epochs

###  HMP ADL Dataset

- Stratified sampling, 16 participants, normalized sensor data
- Results: F1 increased from **91.0% → 96.4%**
- Observation: Sliding windows & chunking significantly improved generalization

###  REALDISP Dataset

Evaluated under three conditions:

1. **Ideal → Ideal**: SSL F1 = 0.8749 | RF F1 = 0.8136  
2. **Ideal → Self**: SSL F1 = 0.8857 | RF F1 = 0.8407  
3. **Self → Self**: SSL F1 = 0.8905 | RF F1 = 0.8321  

 **Conclusion**: SSL consistently outperformed RF across scenarios, confirming the power of pre-trained models in adapting to real-world HAR tasks.

---

##  Repository Contents

- `adl_analysis/`: ADL dataset fine-tuning & evaluation
- `hmp_analysis/`: Preprocessing & fine-tuning on HMP ADL dataset
- `realdisp_analysis/`: Multi-scenario evaluation of SSL vs. RandomForest
- `models/`: Pre-trained HaRNet10 checkpoint & classifier configs
- `notebooks/`: Google Colab notebooks for live experiments

---

##  Acknowledgments

This work builds upon the research and open resources provided by **OxWearables**. All credit for pre-trained models, SSL tasks, and datasets goes to their original authors. This repo represents an independent evaluation and derivative analysis.

---

##  References & Links

- [OxWearables GitHub](https://github.com/OxWearables/ssl-wearables)
- [ADL Dataset GitHub](https://github.com/OxWearables/ssl-wearables/tree/main/data/adl_30hz_clean)
- [HMP ADL UCI Repository](https://archive.ics.uci.edu/ml/datasets/Heterogeneity+Activity+Recognition)
- [REALDISP UCI Repository](https://archive.ics.uci.edu/ml/datasets/Real+Disp+Activity+Dataset)
- [Colab Notebooks – ADL Analysis](https://colab.research.google.com/drive/18E_X3tdH7x4G6SIAQlCzbqk1DN2dpfQn)
- [Colab Notebooks – HMP ADL Analysis](https://colab.research.google.com/drive/13_AExCpZzUHA-17wQD5VqbwTUly9ZnnO)
- [Colab Notebooks – REALDISP (SSL)](https://colab.research.google.com/drive/1BivNJk3OOS_ke3MWtUK9eujCmrPdxtad#scrollTo=fhWeaXjVYhwv)
- [Colab Notebooks – REALDISP (RF)](https://colab.research.google.com/drive/1GxfJVhloY4prENPCtGRjyCPrwVZfDrTI#scrollTo=EFEWaexVV5Mf)

---

##  Contact

For questions, feel free to reach out: [abideep.singh97@gmail.com](mailto:abideep.singh97@gmail.com)
