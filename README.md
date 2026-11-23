# Commercial Activity Pattern Analysis in Saudi Arabia Using Clustering Techniques

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/danah25/danah25.github.io/blob/main/Commercial_Activity_Clustering.ipynb)

## Overview
Commercial activity in Saudi Arabia is expanding rapidly under Vision 2030, yet the spatial distribution of business types across municipalities is not always clear to urban planners and investors. This project applies unsupervised data mining (clustering) techniques to official commercial licensing data to uncover hidden commercial profiles across Saudi municipalities.

This project was developed for **IS 463: Introduction to Data Mining** at the College of Computer and Information Sciences (CCIS), Information Systems Department, King Saud University.

## Dataset
- **Source:** Commercial Activities Open Data – Ministry of Municipalities and Housing (Balady), Saudi Open Data Portal (Q1 2022)
- **Size:** 115,563 commercial license records and 13 attributes
- **Coverage:** 17 Amanat, 376 municipalities, 1,510 activity types, and 1,091 ISIC codes (76,424 renewals and 39,139 new licenses)

## Methodology
### 1. Data Preprocessing
- Removed 2,881 duplicate records (`115,563 → 112,682` records).
- Repaired 67 ISIC codes missing leading zeros and extracted 2-digit ISIC divisions (75 sectors).
- Aggregated records into activity-share profiles across 376 municipalities.
- Converted raw counts into proportions (normalization) and removed constant features.
- Engineered derived attributes: activity diversity, dominant activity percentage, new-license percentage, and average license duration.

### 2. Clustering Algorithms Compared
Using Python and `scikit-learn`, three clustering algorithms were evaluated across `k = 2..10`:
- **K-Means** (centroid-based partitioning)
- **K-Medoids (PAM)** (medoid-based partitioning, Euclidean & Manhattan distances)
- **AGNES** (Agglomerative Hierarchical Clustering – Single, Complete, Average, and Ward linkage)

### 3. Evaluation Metrics
- **Silhouette Score** (higher is better)
- **Davies-Bouldin Index (DBI)** (lower is better)

## Key Results
**K-Means with `k = 3`** achieved the best overall clustering performance (`Silhouette = 0.3544`, `DBI = 1.0947`) compared to K-Medoids (`0.2306`, `1.2603`) and AGNES Ward (`0.1768`, `1.3734`), identifying three distinct municipal commercial profiles:

| Cluster | Municipalities | Dominant Profile | Notable Examples |
| :---: | :---: | :--- | :--- |
| **Cluster 0** | 312 | Mixed Commercial (Retail 34%, Food Services 16% – highest diversity) | General urban/regional municipalities |
| **Cluster 1** | 57 | Retail-Dominated Historic & Market Centers (Retail 58%) | Al-Balad (Jeddah), Central Makkah, Haram Area (Madinah) |
| **Cluster 2** | 7 | Food & Hospitality / Tourism & Pilgrimage Areas (Food Services 74%) | Al-Hada (Taif), Holy Sites (Al-Masha'er) |

## Repository Contents
- `Commercial_Activity_Clustering.ipynb` – Complete Jupyter Notebook containing data exploration, preprocessing, correlation analysis, clustering experiments, and visualizations.

## Team Members (Group 5)
- Shaden Alnuman
- Bayan Almubaddel
- Amjad Almalki
- Danah Alsawat
- Renad Alqarni

## Tools and Libraries
- Python 3
- Scikit-learn
- Pandas & NumPy
- Matplotlib & Seaborn
- Google Colab
