# Identify Customer Segments

Unsupervised learning project that analyzes demographics data from Bertelsmann Arvato Analytics to identify core customer segments for a German mail-order company. By comparing population-wide clusters with customer clusters, the project reveals which demographic groups are over- or under-represented among existing customers — insights that can drive targeted marketing campaigns.

## Overview

The goal is to find **which segments of the German population are most likely to be customers** of a mail-order sales company. The approach:

1. **Preprocessing** — Clean ~891K rows × 85 features of demographics data: convert missing-value codes to NaN, drop columns with >18% missing data, remove rows with >30 missing values, re-encode categorical features, and engineer new features from mixed-type columns.
2. **Dimensionality Reduction** — Apply StandardScaler + PCA to reduce the feature space while retaining the most informative variance.
3. **Clustering** — Use K-Means (k=12) on the general population data to discover natural demographic groupings.
4. **Customer Mapping** — Project ~192K customer records into the same PCA/cluster space (without re-fitting) and compare cluster proportions against the general population to identify over-represented (target audience) and under-represented segments.

## Key Techniques

- **Missing data analysis** at both column and row level, with threshold-based filtering
- **Feature engineering** on mixed-type variables (`PRAEGENDE_JUGENDJAHRE` → decade + movement; `CAMEO_INTL_2015` → wealth + life stage)
- **One-hot encoding** for multi-level categoricals
- **PCA** for dimensionality reduction
- **K-Means clustering** (k=12) with elbow-method selection
- **Cluster distribution comparison** between general population and customers

## Data

Provided by Bertelsmann Arvato Analytics (not included in this repo):

| File | Description |
|---|---|
| `Udacity_AZDIAS_Subset.csv` | Demographics data for the general German population (891,211 × 85) |
| `Udacity_CUSTOMERS_Subset.csv` | Demographics data for mail-order customers (191,652 × 85) |
| `Data_Dictionary.md` | Feature descriptions and value meanings |
| `AZDIAS_Feature_Summary.csv` | Feature types and missing-value codes (85 × 4) |

## Tech Stack

- Python 3
- pandas, NumPy
- scikit-learn (PCA, KMeans, StandardScaler)
- Matplotlib, Seaborn
- Jupyter Notebook

## Project Structure

```
├── Identify_Customer_Segments.ipynb   # Full analysis notebook
├── README.md
```

## Results

By comparing cluster proportions, specific demographic segments were identified as strongly over-represented among customers (target audiences for marketing) and others as under-represented (non-target demographics). These insights enable the company to focus marketing spend on the population segments most likely to convert.

## License

This project was completed as part of the Udacity Data Science Nanodegree. The datasets are proprietary to Bertelsmann Arvato Analytics and are not redistributable.
