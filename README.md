# Cryptocurrency Clustering with K-Means and PCA

## Overview
This project uses unsupervised machine learning techniques to cluster cryptocurrencies based on their price change data over different timeframes. The analysis leverages the **K-Means Clustering** algorithm and **Principal Component Analysis (PCA)** for dimensionality reduction to optimize clustering.

## Objectives
The primary goal of this analysis is to determine whether cryptocurrencies can be grouped into meaningful clusters based on their short-term and long-term price changes.

## Dataset
The dataset used in this challenge contains the following columns:
- **coin_id**: Unique identifier for each cryptocurrency.
- **price_change_percentage_24h**: Percentage change in price over the past 24 hours.
- **price_change_percentage_7d**: Percentage change in price over the past 7 days.
- **price_change_percentage_14d**: Percentage change in price over the past 14 days.
- **price_change_percentage_30d**: Percentage change in price over the past 30 days.
- **price_change_percentage_60d**: Percentage change in price over the past 60 days.
- **price_change_percentage_200d**: Percentage change in price over the past 200 days.
- **price_change_percentage_1y**: Percentage change in price over the past year.

## Process

### 1. Data Preprocessing
- The dataset was loaded into a Pandas DataFrame and inspected for missing values and consistency.
- The numeric columns were scaled using **`StandardScaler`** to normalize the data.

### 2. Finding the Optimal Number of Clusters (Elbow Method)
- The Elbow Method was applied to the scaled data to determine the optimal number of clusters, \( k \).
- The **inertia** values (sum of squared distances of points to their closest cluster center) were computed for \( k \) values ranging from 1 to 11.
- The optimal \( k \) was determined by identifying the "elbow" point on the curve, which minimized inertia while avoiding overfitting.

### 3. K-Means Clustering
- Cryptocurrencies were clustered using the optimal \( k \).
- A scatter plot of the clusters was created, showing **24-hour price changes** vs. **7-day price changes**, with cluster labels.

### 4. Dimensionality Reduction with PCA
- Principal Component Analysis (PCA) was applied to reduce the dataset to 3 components.
- The explained variance ratio was analyzed to ensure the reduced components retained a high percentage (e.g., >90%) of the original variance.
- The Elbow Method was repeated on the PCA-transformed data to find the optimal \( k \) in the reduced feature space.

### 5. Visualizing Clusters with PCA
- Scatter plots of the clusters were created in the PCA-transformed feature space, showing **PC1** vs. **PC2** for easy visualization.

## Results

### Elbow Curve Analysis
- The optimal \( k \) (number of clusters) was determined to be **3** for both the original scaled data and PCA-transformed data.

### Explained Variance
- The total explained variance of the first three principal components was approximately **95%**, indicating that PCA effectively reduced dimensionality while preserving most of the information.

### Clustering Results
- Cryptocurrencies were successfully grouped into **3 clusters**, highlighting distinct patterns in price changes across different timeframes.
- The PCA-transformed clustering provided similar results to the original data clustering, confirming the effectiveness of dimensionality reduction.

## Dependencies
The following Python libraries were used in this project:
- `pandas`: Data manipulation and analysis
- `hvplot`: Interactive visualizations
- `matplotlib`: Static visualizations
- `scikit-learn`: Machine learning and data preprocessing
- `holoviews`: For interactive plotting with `hvplot`

Install dependencies via pip:
```bash
pip install pandas hvplot holoviews scikit-learn matplotlib
# CryptoClustering