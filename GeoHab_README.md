# 🌊 GeoHab 2026 MLWG – Benthic Habitat Prediction

## 📌 Overview

This repository contains my solution for the **GeoHab 2026 Machine Learning Working Group (MLWG) competition**, focused on predicting benthic habitat classes from multibeam echosounder (MBES) data.

Benthic habitats are physically distinct regions of the seafloor associated with specific biological communities, and mapping them is crucial for marine planning, conservation, and resource management.

---

## 🎯 Problem Statement

Given:
- Spatial coordinates (`x`, `y`)
- Multibeam raster data (bathymetry & backscatter)

Task:
> Predict the **benthic habitat class** at unseen locations.

---

## 🧠 Approach

The solution focuses on **geospatial feature engineering + model stability**, rather than complex modeling.

### 🔹 1. Feature Engineering

- Extracted raster values (bathymetry, backscatter)
- Designed **grid-based spatial features** (key driver of performance)
- Explored:
  - Terrain features (slope, curvature)
  - Texture features (GLCM)
  - Clustering-based features  

👉 Most complex features **did not generalize well**

---

### 🔹 2. Modeling

- Model: **LightGBM**
- Stratified K-Fold Cross Validation
- Weighted F1-score optimization

---

### 🔹 3. Stability Improvements

- Seed averaging (multiple random states)
- Feature pruning (removed unstable features)
- Careful CV vs LB validation tracking

---

### 🔹 4. External Signal

- Integrated **publicly shared CNN-based OOF predictions (by Matteo)** as an additional feature  
- Helped capture spatial patterns not easily modeled with tabular features

---

## 📊 Results

| Metric | Score |
|------|------|
| Public Leaderboard |  Rank 1 |
| Private Leaderboard | Rank 13 |

---

## ⚠️ Generalization Insight

A gap between public and private leaderboard performance highlights:

- Sensitivity to spatial distribution shifts  
- Limitations of standard cross-validation for geospatial tasks  
- Importance of **robust validation strategies**

---

## 🔍 Key Learnings

- **Spatial scale matters more than feature complexity**
- Simple grid-based features outperformed advanced engineered features
- Many features (clustering, terrain, texture) led to overfitting
- Model stability (ensembling, seeds) provided consistent gains
- CV ≠ LB in geospatial problems → validation must be carefully designed

---

## 📁 Repository Structure

```
GeoHab-2026-MLWG-Competition/
│
├── Experiments/      # All experimentation notebooks
├── Submissions/      # Final submissions & predictions
├── EDA/       
└── README.md
```

---

## 🔗 Resources

- Kaggle Notebook:  
  https://www.kaggle.com/code/adwaittagalpallewar/geohab-2026-grid-spatial-ml-pub1-pvt13  

- GitHub Repo:  
  https://github.com/CheeseCakeyy/GeoHab-2026-MLWG-Competition  

---

## 🙌 Acknowledgements

- GeoHab MLWG organizers for hosting the competition  
- Matteo for sharing CNN-based OOF predictions  
- Community participants for discussions and insights  

---

## 🚀 Future Work

- Spatial cross-validation (block CV)
- Better handling of spatial distribution shifts
- Hybrid deep learning + tabular approaches
- Interactive geospatial visualization tools

---

## 💬 Final Thoughts

This competition was a great learning experience — from understanding geospatial data to building a complete ML pipeline.

Beyond the technical side, engaging with the community was equally valuable.

This project marks my starting point in geospatial machine learning 🚀
